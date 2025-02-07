## To connect DBT to SNOWFLAKE 

First do we have to create a new project in VS studio 

after the project is created in VS studio do we install the dbt package: 
```python
pip install dbt-snowflake
```

```python
mkdir my_dbt_project 
```
When the directory is created in VS studio do we have to set our direction to the directory

```python
cd my_dbt_project
```

when this is in scope do we create our project with the init function in the terminal 

```python
dbt init dbt_snoflake
```
When we use the dbt init in the terminal do we get requirements that we have to ensure is right to connect to the correct SNOWFLAKE db

## From Snowflake to DBT to Snowflake
after we have created a project and set the folder to our directory do we find the correct schema wi will clean and create a pipeline through. 

then we write a SQL CTE to create the correct name to the correct attribute. 

however, we are creating folders as sr(source) and dim() to each core layer

## Materialized sql 
dbt_yalla.yml
```python
models:
  dbtyalla:
    +materialized: view
    dim:
      +materialized: table
    src:
      +materialized: ephemeral
```
### Materialized Incremental
```python
{{
config(
materialized = 'incremental',
on_schema_change='fail'
)
}}
WITH src_reviews AS (
SELECT * FROM {{ ref('src_reviews') }}
)
SELECT * FROM src_reviews
WHERE reviews is not null
{% if is_incremental() %}
AND date > (select max(date) from {{ this }})
{% endif %}
```

### Materialized Ephemeral
- Understand how models can be connected 
- Understand the four bult-in materializations 
- Understand how materializations can be configured on the file and project level
- Use dbt run with extra parameters. 

#### View: 
##### Use it: 
- You want a lightweight representation  
- You don't reuse data too often 
##### Dont use it: 
- You read from the same model several times

#### Table: 
##### Use it: 
- You read from this model repeatedly 

##### Dont use it: 
- Building single-use models 
- Your model is populated incrementally 

#### Incremental (table appends) 
##### Use it: 
- Fact tables 
- Appends to tables 

##### Dont use it: 
- You want to update historical records


#### Ephemeral (CTEs): 
##### Use it: 
- You merely want an alias to your date 

##### Dont use it: 
You read from the same model several times 


```python
WITH l AS (
    SELECT * 
    FROM {{ ref("dim_listings_cleansed") }}
),

h AS (
    SELECT * 
    FROM {{ ref("dim_hosts_cleansed") }}
)

SELECT
l.listing_id,
l.listing_name,
l.room_type,
l.minimum_nights,
l.price,
l.host_id,
h.host_name,
h.is_superhost AS host_is_superhost,
l.created_at,
GREATEST(l.updated_at, h.updated_at) AS updated_at

FROM l
LEFT JOIN h 
ON h.host_id = l.host_id
```


# Sources and Seeds 

To make our project much more easier and structured do we have to connect it to our sources:

```python
version: 2

sources:
  - name: airbnb
    schema: raw
    tables:
      - name: listings
        identifier: raw_listings

      - name: hosts
        identifier: raw_hosts

      - name: reviews
        identifier: raw_reviews
        loaded_at_field: date
        freshness:
          warn_after: {count: 1, period: hour}
          error_after: {count: 24, period: hour}
```

# Snapshots 
	- Understand how dbt handles type-2 slowly changing dimension 
	- Understanding snapshot strategies 
	- Learning how to create snapshots on top of our listings and host models 

## Snapshot overview: 
Snapshots in dbt are used to track changes to records in your source data over time. They enable slowly changing dimensions (SCD) functionality by capturing and storing historical versions of data. This is particularly useful when your source data changes frequently, but you need to maintain a historical record for analysis.

## How snapshot works in DBT
1.	Define a Snapshot:
- You create a snapshot file in your snapshots directory, specifying:
- The source data.
- The unique identifier for each record.
- The conditions under which dbt should detect changes.

2.	dbt Executes Snapshots:
- When you run dbt snapshot, dbt checks the source data for changes.
- 	New rows or updates to existing rows are captured in the snapshot table.

3.	Snapshot Table:
-	dbt stores snapshots in your data warehouse as a table.
-	Each record includes metadata about when it was inserted and (optionally) when it was updated.

4.	Incremental Updates:
-	Snapshots are incremental, meaning only changes since the last dbt snapshot run are appended to the table

```sql
{% snapshot customer_snapshot %}

--Source table
{{
    config(
        target_schema='snapshots',  -- Where the snapshot table is stored
        unique_key='customer_id',  -- Unique identifier for each record
        strategy='timestamp',      -- Strategy to detect changes
        updated_at='updated_at'    -- Timestamp column to track updates
    )
}}

SELECT
    customer_id,
    name,
    address,
    updated_at
FROM {{ source('raw', 'customer_data') }}

{% endsnapshot %}
```

```sql
{% snapshot scd_raw_listings %}
{{
config(
target_schema='DEV',
unique_key='id',
strategy='timestamp',
updated_at='updated_at',
invalidate_hard_deletes=True
)
}}
select * FROM {{ source('airbnb', 'listings') }}
{% endsnapshot %} 
```

## how it works 
1.	target_schema:
- Specifies where the snapshot table is stored in your warehouse.
2.	unique_key:
-	Identifies the unique record for which changes are tracked.
3.	strategy:
-	"timestamp" compares the updated_at column to detect changes.
4.	Source Query:
-	Pulls data from the customer_data table.

After this have been done do you have to execute the snapshot in the terminal like
```python
dbt snapshot
```

# Tests 
Tests in dbt are assertions that validate your data to ensure its quality, consistency, and accuracy. They are used to catch issues like missing values, duplicates, or invalid relationships before the data is used for analysis or reporting.

## Types of Tests in dbt
1.	Generic Tests:
- Predefined, reusable tests for common data quality checks.
- Examples include:
- unique: Ensures that a column has unique values.
- not_null: Ensures that a column has no null values.
- relationships: Ensures referential integrity between two tables.
- accepted_values: Ensures that column values belong to a predefined set.

2.	Custom Tests:
-	User-defined tests written in SQL to handle specific business logic.
-	Example: Check if all sales records have a valid customer ID.

## How Tests Work in dbt
1.	Defined in schema.yml:
- Tests are defined in the schema.yml file associated with your models or sources.

2.	Executed Using dbt test:
- When you run dbt test, dbt translates these test definitions into SQL queries and executes them against your data warehouse.


### Generic tests 
Generic tests are stored in models folder 

Generic tests are reusable, parameterized tests that validate data based on common data quality rules. They are defined in your schema.yml file and apply directly to specific columns or tables in your models or sources.

Key Characteristics:
- Predefined: dbt provides built-in generic tests (e.g., unique, not_null, relationships, accepted_values).

Customizable: 
- You can write your own generic tests and reuse them across your project.
- Applied in schema.yml: You specify the tests for columns or tables directly in the YAML configuration.

```python
version: 2 

models:
 - name: dim_listings_cleansed
   columns: 
      - name: listing_id
        tests:
          - unique
          - not_null
     
      - name: host_id
        tests:
          - not_null
          - relationships:
              to: ref('dim_host_cleansed')
              field: host_id
    
      - name: room_type
        tests:
          - accepted_values:
              values: ['Entire home/apt',
                       'Private room',
                       'Shared room',
                       'Hotel room']

```

debuging in dbt use the following: 
```python
cat target/compiled/dbtyalla/models/schema.yml/accepted_values_dim_listings_c_b500aa6b2c341d14ad231dae7b4d7d24.sql
```

### Singular Tests: 

Singular tests are stored in the test folder

Singular tests are one-off, model-specific tests written as SQL queries. They are used for custom validation or complex logic that is not covered by generic tests.

#### Key Characteristics:
- Defined in the tests/ Directory: Singular tests are written as SQL files in the tests/ folder.

#### Custom Logic:
- They allow you to write any SQL logic to validate your data.

#### Run Separately:
- Singular tests are executed during dbt test.

|Feature|Generic Tests| Singular Tests|
|-------|-------------|----------------|
|Definition Location| In schema.yml|In tests/as SQL files|
|Reusability|Reusable across models an columns.|One-off, specific to a model|
|Complexity|Best for simple column-level checks|Suitable for complex custom logic|
|Examples|Unique, Not_null, relationships|validity checks, custom constraints|
|Execution|Part of dbt test|Part of dbt test|

## Macros in DBT
Macros in dbt are reusable code snippets written in Jinja, a templating language. They allow you to streamline repetitive logic, enforce best practices, and make your SQL models more modular and maintainable. Essentially, macros are functions that you can call within your dbt project to perform tasks or generate dynamic SQL.

#### Why Use Macros in dbt?
1.	Reusability:
- Write a piece of logic once and use it across multiple models.
2.	Dynamic SQL:
- Create SQL queries that adapt based on parameters, conditions, or context.
3.	Consistency:
- Enforce standard practices by centralizing logic in a macro.
4.	Efficiency:
- Avoid duplicating code and simplify maintenance.


## Documentation in dbt 
Documentation is crucial for you and other to understand what you've been doing in dbt. 
this can be done by two different ways. 

1. do it in your schema.yml and write like this:

```python
version: 2

models:
 - name: dim_list_cleansed
   description: Cleansed table which contains Airbnb listings
   columns:
	- name: listing_id
	  tests:
		- unique
		- not_null 
```

After this is done can you write in the terminal the follwing 
```python
dbt docs geberate
```

otherwise you can use the built in markdown function in dbt and you can do it as followed: 

1. create a new file that names docs.md or something representative
2. then do you write your docs
```python
{% docs dim_listing_cleansed_minimum_nights %}
Minimum number of nights required to rent this property. 

Keep in min that old listings might have `minimum_nights` set to 0 in the source tables. Our cleansed algorithm upadtes this to `1`

{% enddocs%}
```
3. then can you do this in schema.yml
```python
    - name: minimum_nights
        description: '{{doc("docs dim_listing_cleansed_minimum_nights")}}'
        tests:
          - positive_value 
```


or you can use a standalone markdown file that let you insert pictures and flowcharts of the dbt project if needed. 
