FROM linkernetworks/minimal-notebook:master

RUN apt-get update && apt-get install -y \
    git \
    cmake \
    && rm -rf /var/lib/apt/lists/*

RUN conda install --quiet --yes \
    future \
    numpy \
    protobuf \
    && conda clean -tipsy \
    && fix-permissions $CONDA_DIR

RUN git clone --recursive https://github.com/pytorch/pytorch.git /tmp/pytorch \
    && ( cd /tmp/pytorch \
    && python setup_caffe2.py install ) \
    && rm -rf /tmp/*
