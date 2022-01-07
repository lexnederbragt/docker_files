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

ENV PATH="/root/miniconda/bin:$PATH"

RUN conda config --set always_yes yes --set changeps1 no && \
    conda update -q conda && \
    conda info -a

COPY environment.yml .

RUN /bin/bash -c "conda env create --name doconce -f environment.yml"

# add bash kernel
# cannot use `conda activate`, need to use `source activate`
RUN /bin/bash -c "source activate doconce && \
    pip install bash_kernel && \
    python -m bash_kernel.install"
