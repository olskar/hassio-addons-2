ARG BUILD_FROM
FROM $BUILD_FROM

RUN apk add --no-cache jq wget git nodejs nodejs-npm
RUN mkdir -p /usr/src/landroid-bridge
WORKDIR /usr/src/landroid-bridge

RUN cd /usr/src && \
    git clone https://github.com/stefanlaheij/landroid-bridge.git && \
    cd /usr/src/landroid-bridge

RUN apk add --no-cache python make g++ \
    && npm install \
    && npm run clean \
    && npm run grunt \
    && npm prune --production


COPY run.sh /
RUN chmod a+x /run.sh

COPY config_template.json /usr/src/landroid-bridge/config.json

VOLUME /data

EXPOSE 3000

CMD [ "/run.sh" ]
