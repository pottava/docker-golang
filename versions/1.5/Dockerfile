# Golang 1.5.2
# /usr/bin/go version

FROM alpine:3.3

RUN apk --no-cache add go git

RUN mkdir -p /go/src /go/bin && chmod -R 777 /go

ENV GOPATH /go
ENV PATH /go/bin:$PATH
WORKDIR /go
