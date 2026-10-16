FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

ENV DEBIAN_FRONTEND=noninteractive

# Install JAVA V17
RUN apt-get update && apt-get install -y --no-install-recommends openjdk-17-jdk

# Install Nextflow 24
RUN export NXF_VER=24.10.5 && \
    curl -fsSL https://get.nextflow.io | bash && \
    install -m 0755 nextflow /usr/local/bin/nextflow && \
    rm nextflow
