# -*- mode: dockerfile -*-

ARG VERSION=7.17.3

FROM elasticsearch:${VERSION}

USER root

RUN ./bin/elasticsearch-plugin install https://github.com/NLPchina/elasticsearch-analysis-ansj/releases/download/${VERSION}/elasticsearch-analysis-ansj-${VERSION}.0-release.zip

RUN ./bin/elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v${VERSION}/elasticsearch-analysis-ik-${VERSION}.zip

