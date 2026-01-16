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

### Create / sync the environment
```bash
uv sync

## Add a dependency

```bash
uv add pandas sqlalchemy psycopg2-binary click

## Run a Python script

```bash
uv run python ingest_data_exploration.py

## Run Jupyter Notebook

```bash
uv uv run jupyter notebook
