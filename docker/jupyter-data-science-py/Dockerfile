# https://hub.docker.com/r/continuumio/anaconda3/tags
ARG BASE_CONTAINER=continuumio/anaconda3:2020.07
FROM $BASE_CONTAINER

USER root

# Creating directories
RUN mkdir -p /data /notebooks/local

# Setting up volumes
VOLUME ["/data", "/notebooks/local"]

#Set working directory
# WORKDIR /notebooks

COPY requirements.txt /notebooks/requirements.txt
RUN pip install --upgrade pip && pip install -r /notebooks/requirements.txt

# jupyter
EXPOSE 8888

ENTRYPOINT ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--NotebookApp.token=''", "--NotebookApp.password=''", "--notebook-dir=/notebooks", "--no-browser"]
