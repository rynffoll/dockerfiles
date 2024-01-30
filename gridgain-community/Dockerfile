FROM alpine as builder

ARG VERSION=8.8.20
ENV VERSION $VERSION

WORKDIR /opt

RUN apk --no-cache add wget unzip
RUN wget -q https://www.gridgain.com/media/gridgain-community-$VERSION.zip
RUN unzip -q gridgain-community-$VERSION.zip \
    -x "gridgain-community-$VERSION/docs/*" \
    -x "gridgain-community-$VERSION/benchmarks/*" \
    -x "gridgain-community-$VERSION/examples/*" \
    -x "gridgain-community-$VERSION/platforms/*"
RUN mv gridgain-community-$VERSION gridgain-community
RUN wget -q -P gridgain-community -c https://raw.githubusercontent.com/gridgain/gridgain/$VERSION/modules/kubernetes/config/run.sh && \
    chmod +x gridgain-community/run.sh

# # cleanup
# RUN rm -r \
#     gridgain-community/benchmarks \
#     gridgain-community/docs \
#     gridgain-community/examples \
#     gridgain-community/platforms

FROM eclipse-temurin:11-jre
# FROM alpine

# RUN apk --no-cache add bash openjdk11-jre-headless

COPY --from=builder /opt/gridgain-community /opt/gridgain-community

WORKDIR /opt/gridgain-community

ENV IGNITE_HOME /opt/gridgain-community

CMD $IGNITE_HOME/run.sh
