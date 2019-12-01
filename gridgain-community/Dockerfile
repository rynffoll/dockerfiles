FROM alpine as builder

ARG VERSION=8.7.7

WORKDIR /opt
RUN wget https://www.gridgain.com/media/gridgain-community-$VERSION.zip
RUN unzip gridgain-community-$VERSION.zip
RUN mv -v gridgain-community-$VERSION gridgain-community
RUN wget -P gridgain-community https://raw.githubusercontent.com/gridgain/gridgain/master/docker/apache-ignite/run.sh
RUN chmod +x gridgain-community/run.sh

FROM adoptopenjdk:11-jre-hotspot

COPY --from=builder /opt/gridgain-community /opt/gridgain-community

WORKDIR /opt/gridgain-community

ENV IGNITE_HOME /opt/gridgain-community

CMD $IGNITE_HOME/run.sh
