FROM jupyter/datascience-notebook:latest

RUN apt update && apt install -y build-essential

# install additional package...
RUN pip install --no-cache-dir psycopg2-binary \
	python-pachyderm pystardog \
	pandas_profiling pyodbc \
	azure-storage-file-datalake azure-storage-blob \
	azure-storage-file-share

