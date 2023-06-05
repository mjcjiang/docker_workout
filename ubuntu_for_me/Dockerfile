FROM ubuntu:22.04
RUN echo 'APT::Install-Suggests "0";' >> /etc/apt/apt.conf.d/00-docker
RUN echo 'APT::Install-Recommends "0";' >> /etc/apt/apt.conf.d/00-docker
COPY ./sources.list /etc/apt/sources.list
RUN DEBIAN_FRONTEND=noninteractive \
  apt-get update \
  && apt-get install -y python3 \
  && apt-get install -y python3-pip \
  && pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple \
  && apt-get install -y vim \
  && pip install fastapi \
  && pip install uvicorn \
  && apt-get install -y openssh-server \
  && rm -rf /var/lib/apt/lists/*

RUN useradd -ms /bin/bash hjiang
USER hjiang
WORKDIR /home/hjiang
COPY ./main.py /home/hjiang