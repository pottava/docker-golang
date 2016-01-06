# Python 3.5.1
# /usr/bin/python3.5 --version

FROM alpine:3.3

RUN apk --no-cache add go git

RUN mkdir -p /go/src /go/bin && chmod -R 777 /go

ENV GOPATH /go
ENV PATH /go/bin:$PATH
WORKDIR /go
