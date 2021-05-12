FROM jupyter/datascience-notebook:latest

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends unixodbc-dev && \
    wget https://dl.min.io/client/mc/release/linux-amd64/mc && \
    chmod +x mc && \
    mv mc /usr/bin

RUN pip install --upgrade jupyterlab jupyterlab-git

# install additional package...
RUN pip install --no-cache-dir psycopg2-binary pywedge farm-haystack

