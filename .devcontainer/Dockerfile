FROM python:3.8-buster

# Install Python 3 and common tools. You can check latest packages using apt policy <package>
RUN apt-get update --yes && apt-get upgrade --yes

# Install dependencies
COPY requirements.txt $BUILD_USER_HOME/requirements.txt