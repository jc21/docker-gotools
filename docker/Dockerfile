# locked to golang:1.22.8 for now
# as there's a bug with qemu and go 1.23
# its meant to be fixed in 1.23.3
# but I guess we'll wait and see
# https://github.com/golang/go/issues/69259
FROM golang:1.22.8 AS go
LABEL maintainer="Jamie Curnow <jc@jc21.com>"

RUN apt-get update \
	&& apt-get install -y bash wget gcc g++ make git sqlite3 jq \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/* \
	&& mkdir /workspace

WORKDIR /workspace

ARG TARGETPLATFORM

# Gotools
COPY scripts /scripts
COPY files/.golangci.yml /.golangci.yml
RUN /scripts/install-tools

RUN git config --global --add safe.directory /workspace
