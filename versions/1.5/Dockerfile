# Golang 1.5.2
# /usr/bin/go version

FROM alpine:3.3

RUN apk --no-cache add go git \
   && mkdir -p /go/src /go/bin \
   && chmod -R 777 /go

ENV GOPATH=/go PATH=/go/bin:$PATH
WORKDIR /go
