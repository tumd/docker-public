FROM alpine:3.5
MAINTAINER thomas at elajt.se

RUN adduser -D user

ADD "https://build.syncthing.net/job/stdiscosrv/2237/artifact/stdiscosrv-linux-amd64-v0.14.25+13-gac46db7.tar.gz" /tmp/stdiscosrv/
RUN  cd /tmp/stdiscosrv \
  && tar -zxvf *.tar.gz --strip-components=1 \
  && mv /tmp/stdiscosrv/stdiscosrv /usr/local/bin/stdiscosrv \
  && rm -r /tmp/stdiscosrv \
  && mkdir /syncthing \
  && chown -R user: /syncthing

WORKDIR /syncthing

USER user

EXPOSE 8443

ENTRYPOINT ["stdiscosrv"]
CMD ["-http", "-db-dsn=/syncthing/stdiscosrv.db", "-stats-file=/syncthing/stats.log"]
