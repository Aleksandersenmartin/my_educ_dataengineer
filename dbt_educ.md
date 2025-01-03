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
