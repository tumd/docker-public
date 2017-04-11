FROM alpine:3.5
MAINTAINER thomas at elajt.se

RUN adduser -D user

ADD "https://build.syncthing.net/job/strelaysrv/623/artifact/strelaysrv-linux-amd64-v0.14.27-rc.2+4-gc205fdd.tar.gz" /tmp/strelaysrv/
RUN  cd /tmp/strelaysrv \
  && tar -zxvf *.tar.gz --strip-components=1 \
  && mv /tmp/strelaysrv/strelaysrv /usr/local/bin/strelaysrv \
  && rm -r /tmp/strelaysrv \
  && mkdir /syncthing \
  && chown -R user: /syncthing

WORKDIR /syncthing

USER user

EXPOSE 22067
EXPOSE 22070

ENTRYPOINT ["strelaysrv"]
CMD ["-pools=", "-provided-by=twan"]
