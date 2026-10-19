FROM mcr.microsoft.com/devcontainers/base:jammy

SHELL ["/bin/bash", "-c"]

RUN wget https://gitlab.com/wtsi-grit/rapid-curation/-/raw/main/rapid_split.pl \
    https://gitlab.com/wtsi-grit/rapid-curation/-/raw/main/rapid_join.pl \
    https://github.com/wtsi-hpag/PretextView/releases/download/0.2.5/PretextView_Linux-x86-64.zip

RUN unzip PretextView_Linux-x86-64.zip
