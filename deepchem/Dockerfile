FROM jupyter/minimal-notebook:latest

USER root

ARG conda_env=deepchem
ARG py_ver=3.8

# you can add additional libraries you want conda to install by listing them below the first line and ending with "&& \"
#RUN conda create --quiet --yes -p $CONDA_DIR/envs/$conda_env python=$py_ver ipython ipykernel && \
#    conda clean --all -f -y

# create Python 3.x environment and link it to jupyter
#RUN $CONDA_DIR/envs/${conda_env}/bin/python -m ipykernel install --user --name=${conda_env} && \
#    fix-permissions $CONDA_DIR && \
#    fix-permissions /home/$NB_USER

RUN apt-get update && \
    apt-get install -y --no-install-recommends unixodbc-dev && \
    wget https://dl.min.io/client/mc/release/linux-amd64/mc && \
    chmod +x mc && \
    mv mc /usr/bin

RUN conda install -c conda-forge rdkit fpsim2

RUN python -m pip install -U pip

# any additional pip installs can be added by uncommenting the following line
RUN pip install --no-cache-dir psycopg2-binary \
        python-pachyderm pystardog \
        pandas_profiling pyodbc nibabel nilearn \
        azure-storage-file-datalake azure-storage-blob \
        azure-storage-file-share rdflib rdfframes tqdm \
        networkx ampligraph chembl_webresource_client

RUN pip install --pre --use-deprecated=legacy-resolver deepchem

RUN pip install tensorflow==2.2

# prepend conda environment to path
# ENV PATH $CONDA_DIR/envs/${conda_env}/bin:$PATH

# if you want this environment to be the default one, uncomment the following line:
# ENV CONDA_DEFAULT_ENV ${conda_env}

