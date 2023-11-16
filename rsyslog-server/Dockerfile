FROM alpine:3.18.4

RUN apk update
RUN apk add --no-cache coreutils rsyslog rsyslog-pgsql
RUN apk add --no-cache postgresql15-client

COPY rsyslog.conf /etc/rsyslog.conf

EXPOSE 514/tcp 514/udp

CMD rsyslogd -n -f /etc/rsyslog.conf
