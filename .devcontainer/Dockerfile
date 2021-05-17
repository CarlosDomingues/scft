FROM python:3.8-buster

# Install Python 3 and common tools. You can check latest packages using apt policy <package>
RUN apt-get update --yes && apt-get upgrade --yes

# Install dependencies
WORKDIR /tmp
COPY requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt && \
    rm -rf /tmp/*
