# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.238.1/containers/python-3/.devcontainer/base.Dockerfile

# [Choice] Python version (use -bullseye variants on local arm64/Apple Silicon): 3, 3.10, 3.9, 3.8, 3.7, 3.6, 3-bullseye, 3.10-bullseye, 3.9-bullseye, 3.8-bullseye, 3.7-bullseye, 3.6-bullseye, 3-buster, 3.10-buster, 3.9-buster, 3.8-buster, 3.7-buster, 3.6-buster
ARG VARIANT="3.10-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/python:0-${VARIANT}

RUN pipx install poetry
RUN pipx install commitizen
RUN pipx install chia-dev-tools

# [Choice] Node.js version: none, lts/*, 16, 14, 12, 10
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

ENV CHIA_ROOT=/home/vscode/.chia/testnet10

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
  && apt-get -y install --no-install-recommends ca-certificates curl gnupg

RUN curl -sL https://repo.chia.net/FD39E6D3.pubkey.asc | gpg --dearmor -o /usr/share/keyrings/chia.gpg
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/chia.gpg] https://repo.chia.net/debian/ stable main" | tee /etc/apt/sources.list.d/chia.list > /dev/null

RUN apt-get update && apt-get install chia-blockchain-cli
