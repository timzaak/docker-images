FROM alpine:3

RUN apk add --no-cache \
    mysql-client tzdata rsync postgresql-client curl ossutil gzip
ENTRYPOINT ["crond", "-f"]
