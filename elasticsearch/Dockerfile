# -*- mode: dockerfile -*-


FROM elasticsearch:7.17.3

USER root

RUN ./bin/elasticsearch-plugin install https://github.com/timzaak/elasticsearch-analysis-ansj/releases/download/7.17.3/elasticsearch-analysis-ansj-7.17.3.0-release.zip

RUN ./bin/elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.17.3/elasticsearch-analysis-ik-7.17.3.zip

