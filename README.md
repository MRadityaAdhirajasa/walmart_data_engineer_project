# Walmart Airflow + dbt

This project orchestrates a dbt project and a Databricks job with Apache Airflow.

## Local setup

1. Copy `.env.example` to `.env`.
2. Set strong local values for the Airflow and PostgreSQL secrets, and set
   `DATABRICKS_HOST`, `DATABRICKS_TOKEN`, and `DATABRICKS_JOB_ID`.
3. Start the services with `docker compose up --build`.

The `.env` file is ignored by Git. Do not put credentials in DAGs, dbt profiles,
or committed configuration files. The PostgreSQL password should use
URL-safe characters because it is also used in the Airflow database connection
URL.

If a Databricks token was committed previously, revoke it and create a new one
before publishing or running this project.

The dbt profile and Airflow DAG both read their Databricks settings from the
environment. Run dbt commands from `walmart_project/`.
