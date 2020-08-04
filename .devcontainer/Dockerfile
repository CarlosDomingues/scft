FROM ubuntu:20.04 AS build-base-image

# See https://aka.ms/vscode-remote/containers/non-root-user for details.
ARG BUILD_USER_NAME=vscode
ARG BUILD_USER_HOME=/home/$BUILD_USER_NAME
ARG BUILD_USER_UID=1000
ARG BUILD_USER_GID=1000

# Install Python 3 and common tools. You can check latest packages using apt policy <package>
RUN apt-get update --yes && \
    apt-get install --no-install-recommends --yes \
        curl=7.* \
        fish=3.* \
        git=1:2.25.1-1ubuntu3 \
        jq=1.6-1 \
        python3=3.8.2-0ubuntu2 \
        python3-pip=20.0.2-5ubuntu1 \
        python3-setuptools=45.2.0-1 \
        python3-venv=3.8.2-0ubuntu2 \
        unrar=1:5.6.6-2build1 \
        unzip=6.0-25ubuntu1 && \
    ln --symbolic /usr/bin/python3 /usr/local/bin/python && \
    ln --symbolic /usr/bin/pip3 /usr/local/bin/pip && \
    rm -rf /var/lib/apt/lists/*

# Setup non-root user
RUN groupadd --gid "${BUILD_USER_GID}" \
        "${BUILD_USER_NAME}" && \
    useradd --system \
        --home "${BUILD_USER_HOME}" \
        --uid "${BUILD_USER_UID}" \
        --gid "${BUILD_USER_GID}" \
        --shell /usr/bin/fish \
        "${BUILD_USER_NAME}" && \
    mkdir --parents "${BUILD_USER_HOME}" && \
    chown --recursive "${BUILD_USER_NAME}:${BUILD_USER_NAME}" "${BUILD_USER_HOME}"

# Install dependencies
COPY requirements.txt $BUILD_USER_HOME/requirements.txt

USER ${BUILD_USER_NAME}
WORKDIR ${BUILD_USER_HOME}
SHELL ["/usr/bin/fish", "-c"]
RUN set -Ua fish_user_paths $BUILD_USER_HOME/.local/bin && \
    pip install -r $BUILD_USER_HOME/requirements.txt
