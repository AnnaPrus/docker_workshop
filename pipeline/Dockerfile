FROM python:3.13.11-slim
RUN pip install pandas pyarrow 

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/
WORKDIR /code

ENV PATH="/app/.venv/bin:$PATH"
COPY "pyproject.toml" "uv.lock" ".python-version" ./
RUN uv sync --locked
COPY ingest_data.py .

COPY "pyproject.toml" "uv.lock" ".python-version" ./

ENTRYPOINT ["python", "ingest_data.py"]