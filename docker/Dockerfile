FROM hysds/pge-base:latest

ENV HOME=/home/jovyan \
    CONDA_DIR=/opt/conda

USER root
RUN $CONDA_DIR/bin/conda install -y nb_conda_kernels

USER jovyan
RUN $CONDA_DIR/bin/pip install 'ipykernel<5.0.0'

RUN cd $HOME \
    && git clone https://github.com/hysds/notebook_pge_wrapper.git \
    && cd notebook_pge_wrapper \
    && $CONDA_DIR/bin/pip install -e .

# copy your repo into the docker container
################################################
#COPY . $HOME/<repo name>
COPY . $HOME/hello_world
################################################

WORKDIR $HOME

CMD ["/bin/bash", "--login"]
