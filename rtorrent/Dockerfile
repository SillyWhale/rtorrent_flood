FROM alpine:3.7

RUN \
	apk add -U --no-cache rtorrent supervisor screen && mkdir -p /download/.session/

COPY include/rtorrent.rc /root/.rtorrent.rc
COPY include/supervisord.ini /etc/supervisor.d/supervisord.ini

VOLUME /download
EXPOSE 5000 55000

ENTRYPOINT [ "/usr/bin/supervisord", "-c", "/etc/supervisord.conf" ]