FROM golang:1.24.2-alpine as build
ENV OSSUTIL_VERSION 1.7.19
WORKDIR /go/src/aliyun 
RUN apk add --update --no-cache curl git && \
    curl -Lo /go/src/aliyun/ossutil.zip https://github.com/aliyun/ossutil/archive/refs/tags/v${OSSUTIL_VERSION}.zip && \
    unzip /go/src/aliyun/ossutil.zip && \
    cd ossutil-${OSSUTIL_VERSION} && \
    go get && \
    go build && \
    cp /go/src/aliyun/ossutil-${OSSUTIL_VERSION}/ossutil /

FROM alpine:3 as build2
RUN apk add --update --no-cache mariadb

FROM alpine:3

ENV TZ="Asia/Shanghai"

COPY --from=build /ossutil /usr/local/bin/ossutil
COPY --from=build2 /usr/lib/mariadb/plugin/caching_sha2_password.so /usr/lib/mariadb/plugin/caching_sha2_password.so
RUN apk add --update --no-cache \
    mysql-client postgresql-client \
    curl gzip openssh-client \
    tzdata rsync \
    ca-certificates \
    sshpass

ENTRYPOINT ["crond", "-f"]
