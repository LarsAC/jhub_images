FROM jupyter/datascience-notebook:latest

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    unixodbc-dev

# install additional package...
RUN conda install --quiet --yes psycopg2-binary \
	python-pachyderm pystardog \
	pandas_profiling pyodbc \
	azure-storage-file-datalake azure-storage-blob \
	azure-storage-file-share

