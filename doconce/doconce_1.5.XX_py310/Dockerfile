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
    pandoc \
    ispell \
    locales \
    python-pip \
    build-essential

# pdflatex
RUN sudo apt-get install -qq\
    texlive-latex-base\
    texlive-fonts-recommended\
    texlive-fonts-extra\
    texlive-latex-extra

RUN wget -q https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh &&\
    bash miniconda.sh -b -p /root/miniconda

RUN sudo locale-gen nb_NO.UTF-8; sudo update-locale

ENV PATH="/root/miniconda/bin:$PATH"

RUN conda config --set always_yes yes --set changeps1 no && \
    conda update -q conda && \
    conda info -a

COPY environment.yml .

# generate conda environment
RUN /bin/bash -c "conda env create --name doconce -f environment.yml"

# add bash kernel for Jupyter
RUN /bin/bash -c "source activate doconce && \
    pip install bash_kernel && \
    python -m bash_kernel.install"
