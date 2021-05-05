FROM jupyter/datascience-notebook:latest

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends unixodbc-dev && \
    wget https://dl.min.io/client/mc/release/linux-amd64/mc && \
    chmod +x mc && \
    mv mc /usr/bin

RUN pip install --upgrade jupyterlab jupyterlab-git

# install additional package...
RUN pip install --no-cache-dir psycopg2-binary pywedge \
	python-pachyderm pystardog torch torchvision \
	pandas_profiling pyodbc nibabel nilearn \
	azure-storage-file-datalake azure-storage-blob \
	azure-storage-file-share rdflib rdfframes tqdm networkx \
        gensim spacy scispacy nltk flair bertopic sentence-transformers

