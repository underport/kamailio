FROM pkecastillo/underbian:bullseye

LABEL maintener="Underport <pkecastillo@gmail.com>"

WORKDIR /etc/kamailio

RUN sed -i 's/httpredir/deb/g' /etc/apt/sources.list

RUN rm -rf /var/lib/apt/lists/* && apt-get update &&   DEBIAN_FRONTEND=noninteractive apt-get install -qq --assume-yes gnupg wget
# kamailio repo
RUN echo "deb http://deb.kamailio.org/kamailio56 bullseye main" >   /etc/apt/sources.list.d/kamailio.list
RUN wget -O- http://deb.kamailio.org/kamailiodebkey.gpg | apt-key add -

# IMPORTANTE NO TIENE EL MODULO db_redis.so
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -qq --assume-yes kamailio=5.6.5+bpo11 kamailio-autheph-modules=5.6.5+bpo11 kamailio-berkeley-bin=5.6.5+bpo11 kamailio-berkeley-modules=5.6.5+bpo11 kamailio-cnxcc-modules=5.6.5+bpo11 kamailio-cpl-modules=5.6.5+bpo11 kamailio-dbg=5.6.5+bpo11 kamailio-erlang-modules=5.6.5+bpo11 kamailio-extra-modules=5.6.5+bpo11 kamailio-geoip-modules=5.6.5+bpo11 kamailio-geoip2-modules=5.6.5+bpo11 kamailio-ims-modules=5.6.5+bpo11 kamailio-json-modules=5.6.5+bpo11 kamailio-kazoo-modules=5.6.5+bpo11 kamailio-ldap-modules=5.6.5+bpo11 kamailio-lua-modules=5.6.5+bpo11 kamailio-lwsc-modules=5.6.5+bpo11 kamailio-memcached-modules=5.6.5+bpo11 kamailio-mongodb-modules=5.6.5+bpo11 kamailio-mono-modules=5.6.5+bpo11 kamailio-mqtt-modules=5.6.5+bpo11 kamailio-mysql-modules=5.6.5+bpo11 kamailio-nth=5.6.5+bpo11 kamailio-outbound-modules=5.6.5+bpo11 kamailio-perl-modules=5.6.5+bpo11 kamailio-phonenum-modules=5.6.5+bpo11 kamailio-postgres-modules=5.6.5+bpo11 kamailio-presence-modules=5.6.5+bpo11 kamailio-python-modules=5.6.5+bpo11 kamailio-python3-modules=5.6.5+bpo11 kamailio-rabbitmq-modules=5.6.5+bpo11 kamailio-radius-modules=5.6.5+bpo11 kamailio-redis-modules=5.6.5+bpo11 kamailio-ruby-modules=5.6.5+bpo11 kamailio-sctp-modules=5.6.5+bpo11 kamailio-secsipid-modules=5.6.5+bpo11 kamailio-snmpstats-modules=5.6.5+bpo11 kamailio-sqlite-modules=5.6.5+bpo11 kamailio-systemd-modules=5.6.5+bpo11 kamailio-tls-modules=5.6.5+bpo11 kamailio-unixodbc-modules=5.6.5+bpo11 kamailio-utils-modules=5.6.5+bpo11 kamailio-websocket-modules=5.6.5+bpo11 kamailio-xml-modules=5.6.5+bpo11 kamailio-xmpp-modules=5.6.5+bpo11 sngrep traceroute gettext-base procps
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

COPY ./tools/tls.cfg /etc/kamailio/tls.cfg
COPY ./tools/GeoLite2-City.mmdb /etc/kamailio/GeoLite2-City.mmdb