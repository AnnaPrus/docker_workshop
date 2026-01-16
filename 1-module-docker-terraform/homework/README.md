# Data Engineering Zoomcamp: Homework for Module 1

This repository contains exercises and homework for the **Data Engineering Zoomcamp**.
It focuses on Python environments, Docker, and ingesting Taxi Trips data into Postgres.

## Project Structure

```text
1-module-docker-terraform/
└── homework/
    ├── Dockerfile
    ├── docker-compose.yaml
    ├── ingest_data_exploration.py
    ├── ingest_data_exploration.ipynb
    ├── main.py
    ├── pyproject.toml
    ├── uv.lock
    ├── .python-version
    ├── .gitignore
```

---

## 🐍 Python & uv

This project uses **uv** for Python dependency management.

## Create / sync the environment

```bash
uv sync
```

## Add a dependency

```bash
uv add pandas sqlalchemy psycopg2-binary click
```

## Run a Python script

```bash
uv run python ingest_data_exploration.py
```

## Run Jupyter Notebook

```bash
uv uv run jupyter notebook
```

## Solution for the SQL query part:

```sql
SELECT COUNT(*)
FROM green_trip_data_2025
WHERE lpep_pickup_datetime >= '2025-11-01'
  AND lpep_pickup_datetime < '2025-12-01'
  AND trip_distance <= 1;
```

```sql
SELECT
    DATE(lpep_pickup_datetime) as pick_up_time,
    SUM(trip_distance) AS total_trip_distance
FROM green_trip_data_2025
WHERE trip_distance < 100
GROUP BY pick_up_time
ORDER BY total_trip_distance DESC
LIMIT 1;
```


```sql
SELECT "PULocationID" as pick_up_id, 
 DATE(lpep_pickup_datetime) as pick_up_time, 
 SUM(trip_distance) AS total_trip_distance
 
 FROM green_trip_data_2025
 GROUP BY pick_up_time, pick_up_id
```


```sql
SELECT
    z."Zone" AS pickup_zone,
    SUM(t.total_amount) AS total_revenue
FROM green_trip_data_2025 t
JOIN taxi_zone_lookup z
  ON t."PULocationID" = z."LocationID"
WHERE DATE(t.lpep_pickup_datetime) = '2025-11-18'
GROUP BY z."Zone"
ORDER BY total_revenue DESC
LIMIT 1;
```
