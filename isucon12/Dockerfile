FROM golang:1.22.9-bullseye

WORKDIR /tmp
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
  apt-get install -y --no-install-recommends wget gcc g++ make sqlite3 default-mysql-client && \
  rm -rf /var/lib/apt/lists/*

RUN useradd --uid=1001 --create-home isucon
USER isucon

RUN mkdir -p /home/isucon/webapp/go
WORKDIR /home/isucon/webapp/go
COPY --chown=isucon:isucon ./ /home/isucon/webapp/go/

ENV GOPATH=/home/isucon/tmp/go
ENV GOCACHE=/home/isucon/tmp/go/.cache

CMD ["go", "run", "./cmd/isuports/main.go"]

