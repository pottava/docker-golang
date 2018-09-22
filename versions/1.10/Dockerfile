# Golang v1.10

FROM alpine:3.8

ENV GOPATH=/go \
    PATH=/go/bin:/usr/local/go/bin:$PATH

WORKDIR /go/src

RUN apk --no-cache add --virtual build-dependencies bash gcc musl-dev openssl go git \

    # Install go 1.10
    && GOLANG_VERSION=1.10.4 \
    && GOLANG_SRC_URL=https://golang.org/dl/go$GOLANG_VERSION.src.tar.gz \
    && GOLANG_SRC_SHA256=6fe44965ed453cd968a81988523e9b0e794d3a478f91fd7983c28763d52d5781 \
    && export GOROOT_BOOTSTRAP="$(go env GOROOT)" \
    && wget -q "$GOLANG_SRC_URL" -O golang.tar.gz \
    && echo "$GOLANG_SRC_SHA256  golang.tar.gz" | sha256sum -c - \
    && tar -C /usr/local -xzf golang.tar.gz \
    && cd /usr/local/go/src \
    && ./make.bash \
    && chmod -R 777 /go \

    # Clean up
    && find /usr/local/go -depth -type d -name test -exec rm -rf {} \; \
    && find /usr/local/go -depth -type d -name testdata -exec rm -rf {} \; \
    && find / -depth -type f -name *_test.go -exec rm -f {} \; \
    && find / -depth -type f -name *README* -exec rm -f {} \; \
    && rm -rf /usr/local/go/doc /usr/local/go/api /usr/local/go/misc/trace \
        /usr/local/go/pkg/linux_amd64/vendor \
        /usr/local/go/pkg/linux_amd64/cmd/vendor \
        /usr/local/go/src/cmd/vendor/ \
        /usr/local/go/pkg/obj/go-build /usr/local/go/pkg/bootstrap \
        /go/src/* /var/cache/* /var/lib/apk* \
    && apk del --purge -r build-dependencies

CMD ["go", "version"]
