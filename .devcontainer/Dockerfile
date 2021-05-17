FROM python:3.8-buster

# Update and upgrade base system
RUN apt-get update --yes && apt-get upgrade --yes

# Automatically setup Time Zone
RUN pip install tzupdate

# Install and configure poetry
RUN pip install poetry
ENV PATH="/root/.local/bin:${PATH}"
RUN poetry config virtualenvs.create false && \
    poetry completions bash > /etc/bash_completion.d/poetry.bash-completion

# Install dependencies
WORKDIR /tmp
COPY pyproject.toml /tmp/pyproject.toml
COPY poetry.lock /tmp/poetry.lock
RUN poetry install && \
    rm -rf /tmp/*
