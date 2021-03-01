# syntax = docker/dockerfile:1.2.1
ARG DOCKER_VERSION=20.10.3
FROM docker:${DOCKER_VERSION} AS docker

FROM python:3.9.2-buster
COPY --from=docker /usr/local/bin/docker /usr/local/bin/
WORKDIR /app
RUN apt install openssh-client
RUN --mount=type=cache,target=/root/.cache \ 
    pip3 install molecule[ansible,docker,lint] ansible-lint paramiko yamllint
CMD ansible --version