FROM debian:jessie

RUN apt-get update && apt-get -y install curl \
 && rm -rf /var/lib/apt/lists/* \
 && mkdir -p /opt/mattermost/data \
 && useradd -r mattermost -U \
 && cd /opt \
 && curl https://releases.mattermost.com/3.3.0/mattermost-team-3.3.0-linux-amd64.tar.gz | tar -xvz

RUN rm /opt/mattermost/config/config.json
COPY config.template.json /

COPY docker-entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 80
