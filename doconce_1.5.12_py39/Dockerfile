FROM ubuntu:xenial

RUN apt-get update && \
    apt-get install -qq\
    sudo\
    mercurial\
    git\
    subversion\
    wget\
    apt-utils\
    bzip2 \
    build-essential

RUN wget -q https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh &&\
    bash miniconda.sh -b -p /root/miniconda

ENV PATH="/root/miniconda/bin:$PATH"

RUN conda config --set always_yes yes --set changeps1 no && \
    conda update -q conda && \
    conda info -a

COPY environment.yml .

RUN /bin/bash -c "conda env create --name doconce -f environment.yml"
