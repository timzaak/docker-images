# -*- mode: dockerfile -*-


FROM elasticsearch:7.17.2


RUN ./bin/elasticsearch-plugin install --batch https://github.com/timzaak/elasticsearch-analysis-ansj/releases/download/7.17.2/elasticsearch-analysis-ansj-7.17.2.0-release.zip

RUN ./bin/elasticsearch-plugin install --batch https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.17.2/elasticsearch-analysis-ik-7.17.2.zip

