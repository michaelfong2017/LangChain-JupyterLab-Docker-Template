FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y --no-install-recommends \
  build-essential \
  wget \
  ca-certificates \
  pkg-config \
  && rm -rf /var/lib/apt/lists/*

RUN wget -O Miniforge3.sh "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"

ENV CONDA_DIR=/opt/conda
RUN bash Miniforge3.sh -b -p ${CONDA_DIR}

ENV PATH=${CONDA_DIR}/bin:${PATH}
RUN . ${CONDA_DIR}/etc/profile.d/conda.sh && conda activate base
RUN echo ". ${CONDA_DIR}/etc/profile.d/conda.sh && conda activate base" >> /etc/skel/.bashrc
RUN echo ". ${CONDA_DIR}/etc/profile.d/conda.sh && conda activate base" >> ~/.bashrc

RUN conda update -y conda
RUN conda install -y -c conda-forge conda-libmamba-solver \
  && conda config --set solver libmamba

RUN conda install -y -c conda-forge matplotlib pandas jupyterlab
RUN conda install -y -c conda-forge openai langchain

RUN pip install chromadb tiktoken chromadb-client

RUN mkdir -p /sandbox
WORKDIR /sandbox

EXPOSE 8888

CMD ["/bin/bash", "-c", "jupyter lab --ip=0.0.0.0 --port=8888 --no-browser --allow-root --NotebookApp.token="]