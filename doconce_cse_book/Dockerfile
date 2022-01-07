FROM ubuntu:xenial

RUN apt-get update && \
    apt-get install -qq\
    sudo\
    mercurial\
    git\
    subversion\
    wget\
    apt-utils\
    bzip2

RUN wget -q https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh &&\
    bash miniconda.sh -b -p /root/miniconda

ENV PATH="/root/miniconda/bin:$PATH"

RUN conda config --set always_yes yes --set changeps1 no && \
    conda update -q conda && \
    conda info -a

RUN apt-get install -qq\
    imagemagick\
    netpbm\
    mjpegtools\
    pdftk\
    giftrans\
    gv\
    evince\
    smpeg-plaympeg\
    mplayer\
    totem\
    libav-tools\
    ispell\
    pandoc\
    python-pip\
    idle\
    python-dev\
    python-pdftools

RUN apt-get install -qq\
    texinfo\
    texlive\
    texlive-base\
    texlive-binaries\
    texlive-extra-utils\
    texlive-generic-extra\
    texlive-latex-extra\
    texlive-latex-recommended\
    texlive-math-extra\
    texlive-font-utils\
    texlive-humanities\
    texlive-xetex\
    auctex\
    latexdiff\
    fonts-tlwg-kinnari\
    ttf-ubuntu-font-family

RUN apt-get -qq install locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && locale-gen
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN /bin/bash -c "conda create --name doconce python\<3.7 &&\
        source activate doconce &&\
        conda install future notebook preprocess publish -c defaults -c conda-forge &&\
        pip install mako pygments &&\
        git clone https://github.com/CINPLA/doconce &&\
        cd doconce &&\
        git checkout cse &&\
        pip install ."

RUN apt-get -qq install fonts-noto
