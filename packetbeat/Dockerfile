FROM phusion/baseimage:latest

ENV VERSION=6.1.2 ARCH=amd64 EXTENSION=deb
ENV FILENAME=packetbeat-${VERSION}-${ARCH}.${EXTENSION}

RUN apt-get update
RUN apt-get -y -q install libpcap0.8 wget
RUN wget https://artifacts.elastic.co/downloads/beats/packetbeat/${FILENAME}
RUN dpkg -i ${FILENAME}

WORKDIR packetbeat-${VERSION}
#ADD config/packetbeat.yaml packetbeat.yml

COPY config/packetbeat.yml /etc/packetbeat/packetbeat.yml
#RUN chmod go-w /etc/packetbeat/packetbeat.yaml


CMD ["./packetbeat"]
