# syntax=docker/dockerfile:1
ARG FROM_IMAGE
FROM ${FROM_IMAGE} as original

RUN /bin/bash -c "echo dummy build"

FROM original as tools

RUN  /bin/bash -c "echo apt-get: installing build-essential htop \
  && apt-get update && apt-get install -y \
    build-essential \
    htop \
  && rm -rf /var/lib/apt/lists/* \
"
RUN  /bin/bash -c "echo preparing the history saving \
  && echo '' >> $HOME/.bashrc \ 
  && cat $HOME/.bashrc | grep -v HIST > /tmp/.bashrc \ 
  && mv /tmp/.bashrc $HOME/.bashrc \
  && source $HOME/.bashrc \
  "

RUN  /bin/bash -c "echo pip: installing pylint ipykernel \
  # && export PATH=/opt/conda/envs/rapids/bin:$PATH \
  && pip install pylint ipykernel \
  " 

FROM tools as libs

# Some old examples

# RUN  /bin/bash -c "echo apt-get: installing libsndfile1 ffmpeg \
#   && apt-get update && apt-get install -y \
#     libsndfile1 \
#     ffmpeg \
#     sox \
#     libcurl4-openssl-dev \
#     libsox-dev \
#   && rm -rf /var/lib/apt/lists/* \
# "

# RUN  /bin/bash -c "echo pip: installing nemo \
#   # && export PATH=/opt/conda/envs/rapids/bin:$PATH \
#   && pip install Cython \
#   && pip install nemo_toolkit[all] nemo-asr \
#   # && pip install git+git://github.com/pytorch/audio.git@82e02e85336 \
#   && pip install --no-deps torchaudio==0.5.0 \
#   && pip install git+https://github.com/NVIDIA/PyProf@master \
#   " 

RUN /bin/bash -c "echo dummy build"

FROM libs as final

RUN /bin/bash -c "echo dummy build"
