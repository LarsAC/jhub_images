FROM jupyter/minimal-notebook:latest

USER root

ARG conda_env=python38
ARG py_ver=3.8

# you can add additional libraries you want conda to install by listing them below the first line and ending with "&& \"
RUN conda create --quiet --yes -p $CONDA_DIR/envs/$conda_env python=$py_ver ipython ipykernel && \
    conda clean --all -f -y

# create Python 3.x environment and link it to jupyter
RUN $CONDA_DIR/envs/${conda_env}/bin/python -m ipykernel install --user --name=${conda_env} && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

# any additional pip installs can be added by uncommenting the following line
# RUN $CONDA_DIR/envs/${conda_env}/bin/pip install 

# prepend conda environment to path
ENV PATH $CONDA_DIR/envs/${conda_env}/bin:$PATH

# if you want this environment to be the default one, uncomment the following line:
# ENV CONDA_DEFAULT_ENV ${conda_env}

RUN apt-get update && \
    apt-get install -y --no-install-recommends unixodbc-dev && \
    wget https://dl.min.io/client/mc/release/linux-amd64/mc && \
    chmod +x mc && \
    mv mc /usr/bin

# install additional package...
RUN pip install --no-cache-dir psycopg2-binary \
	python-pachyderm pystardog \
	pandas_profiling pyodbc nibabel nilearn \
	azure-storage-file-datalake azure-storage-blob \
	azure-storage-file-share rdflib rdfframes tqdm \
        networkx ampligraph

