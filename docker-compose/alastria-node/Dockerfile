FROM adoptopenjdk/openjdk11:alpine-jre

RUN apk add --no-cache tar jq

WORKDIR /data/alastria-node-besu

ENV VERSION_BESU="22.10.3"
RUN wget https://hyperledger.jfrog.io/artifactory/besu-binaries/besu/$VERSION_BESU/besu-$VERSION_BESU.tar.gz -O - | tar -xz

RUN ln -s /data/alastria-node-besu/besu-$VERSION_BESU/bin bin
RUN ln -s /data/alastria-node-besu/besu-$VERSION_BESU/lib lib

COPY entrypoint.sh checkForUpdates.sh /usr/local/bin/
RUN ["chmod", "+x", "/usr/local/bin/entrypoint.sh", "/usr/local/bin/checkForUpdates.sh"]

ENTRYPOINT [ "/usr/local/bin/entrypoint.sh" ]
