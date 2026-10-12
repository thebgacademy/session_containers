# Session Containers

This repo is the BGA container Monorepo. 
All custom Dockerfiles needed for sessions should be committed to this repository.

This will help with:
- Security - Ensuring that containers are reviewed
- Speed - in setting up Codespaces, so we are not relying solely on Codespaces building at session start
- Maintenance - Keeping them all in one place means we can keep a better eye on the containers for various sessions

### Actions
Some github actions have been set up so that each folder (e.g. session) containing a Dockerfile will have a docker image built and stored on GHCR.io (Github container registry).

This should take the form of:
- https://ghrc.io/thebgacademy/{folder_name}:latest
- https://ghrc.io/thebgacademy/{folder_name}:{sha commit}

### Example

At commit https://github.com/thebgacademy/easel-and-entap/commit/4703e4e2f7b54c4834177daafcaebac6b3982c12, the Easel session from 2024 now has a Dockerfile (as we have moved away from GitPod). This file is based off of the Microsoft image suggested for codespaces, so should be retained where possible.

However, we need to make sure that the image has a specific version of JAVA and Nextflow. So we extend the image with the Dockerfile.

In this case, the ENV flag tells the operating system in the container that it can't wait for human interaction (so it should always install what we tell it to via apt).

```
FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

ENV DEBIAN_FRONTEND=noninteractive

# Install JAVA V17
RUN apt-get update && apt-get install -y --no-install-recommends openjdk-17-jdk

# Install Nextflow 24
RUN export NXF_VER=24.10.5 && \
    curl -fsSL https://get.nextflow.io | bash && \
    install -m 0755 nextflow /usr/local/bin/nextflow && \
    rm nextflow
```
