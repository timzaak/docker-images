FROM golang:1.24.2-alpine as build
ENV OSSUTIL_VERSION 1.7.19
WORKDIR /go/src/aliyun 
RUN apk add --update --no-cache curl git && \
    curl -Lo /go/src/aliyun/ossutil.zip https://github.com/aliyun/ossutil/archive/refs/tags/v${OSSUTIL_VERSION}.zip && \
    unzip /go/src/aliyun/ossutil.zip && \
    cd ossutil-${OSSUTIL_VERSION} && \
    go get && \
    go build && \
    cp /go/src/aliyun/ossutil-${OSSUTIL_VERSION}/ossutil-${OSSUTIL_VERSION} / 

FROM alpine:3

ENV TZ="Asia/Shanghai"

COPY --from=build /ossutil-${OSSUTIL_VERSION} /usr/local/bin/ossutil
#RUN apk update
RUN apk add --update --no-cache \
    mysql-client tzdata rsync postgresql-client curl gzip


ENTRYPOINT ["crond", "-f"]
