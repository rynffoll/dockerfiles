FROM alpine as builder

ARG GG_VERSION=8.8.20
ENV GG_VERSION $GG_VERSION

WORKDIR /opt

RUN apk --no-cache add wget unzip
RUN wget -q https://www.gridgain.com/media/gridgain-community-$GG_VERSION.zip
RUN unzip -q gridgain-community-$GG_VERSION.zip
RUN mv gridgain-community-$GG_VERSION gridgain-community
RUN wget -P gridgain-community -c https://raw.githubusercontent.com/gridgain/gridgain/$GG_VERSION/modules/kubernetes/config/run.sh
RUN chmod +x gridgain-community/run.sh

FROM eclipse-temurin:11-jre

COPY --from=builder /opt/gridgain-community /opt/gridgain-community

WORKDIR /opt/gridgain-community

ENV IGNITE_HOME /opt/gridgain-community

CMD $IGNITE_HOME/run.sh
