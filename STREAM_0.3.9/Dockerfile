############################################################
# Dockerfile to build STREAM v0.3.9
############################################################

# Set the base image to anaconda python
FROM continuumio/miniconda3

# File Author / Maintainer
MAINTAINER Huidong Chen

ENV SHELL bash

RUN conda config --add channels defaults
RUN conda config --add channels conda-forge
RUN conda config --add channels bioconda

RUN apt-get update && apt-get install gsl-bin libgsl0-dev -y && apt-get clean

#Install stream package
RUN conda install libgfortran tzlocal stream=0.3.9 -y && conda clean --all -y
RUN Rscript -e 'install.packages("stringi",repos="https://cloud.r-project.org/")'

#steps to sync with master on github
#RUN packagepath=$(python -c "import stream; print(stream.__path__[0])") && rm -rf ${packagepath}*
#RUN git clone https://github.com/pinellolab/STREAM.git && cd STREAM && python setup.py install && cd .. && rm -Rf STREAM

#run_test
RUN python -c "import stream; print(stream.__version__)"
#RUN stream_run_test


ENTRYPOINT ["stream"]

