FROM postgres:9.6
MAINTAINER Mike Dillon <mike@appropriate.io>

ENV PGROUTING_VERSION 2.3.2+ds-2
ENV POSTGIS_MAJOR 2.3
ENV POSTGIS_VERSION 2.3.1+dfsg-2

RUN apt-get update \
      && apt-get install -y --no-install-recommends \
           postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR \
           postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR-scripts \
           postgis \
           postgresql-$PG_MAJOR-pgrouting \
      && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /docker-entrypoint-initdb.d
COPY ./initdb-postgis.sh /docker-entrypoint-initdb.d/postgis.sh
COPY ./update-postgis.sh /usr/local/bin

