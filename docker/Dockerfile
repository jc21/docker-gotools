FROM golang:latest as go

LABEL maintainer="Jamie Curnow <jc@jc21.com>"

RUN apt-get update \
	&& apt-get install -y bash wget gcc g++ make git sqlite3 jq \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/* \
	&& mkdir /workspace

WORKDIR /workspace

# Gotools
COPY scripts /scripts
COPY files/.golangci.yml /.golangci.yml
RUN /scripts/install-tools

RUN git config --global --add safe.directory /workspace

