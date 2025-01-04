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
