FROM alpine as builder

FROM adoptopenjdk:11-jre-hotspot

COPY build/gridgain-community /opt/gridgain-community

WORKDIR /opt/gridgain-community

ENV IGNITE_HOME /opt/gridgain-community

CMD $IGNITE_HOME/run.sh
