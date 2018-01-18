FROM phusion/baseimage:latest

ENV VERSION=6.1.2 ARCH=amd64 EXTENSION=deb
ENV FILENAME=packetbeat-${VERSION}-${ARCH}.${EXTENSION}

RUN apt-get update
RUN apt-get -y -q install libpcap0.8 wget
#https://artifacts.elastic.co/downloads/beats/packetbeat/packetbeat-6.1.2-amd64.deb
RUN wget https://artifacts.elastic.co/downloads/beats/packetbeat/${FILENAME}
RUN dpkg -i ${FILENAME}

WORKDIR packetbeat-${VERSION}
ADD config/packetbeat.yaml packetbeat.yaml

COPY config/packetbeat.yaml /etc/packetbeat/packetbeat.yaml

CMD ["./packetbeat"]
#FROM docker.elastic.co/beats/packetbeat:6.1.2
#COPY config/packetbeat.yaml /usr/share/packetbeat/packetbeat.yaml
#USER root
#RUN chown packetbeat /usr/share/packetbeat/packetbeat.yaml
#USER packetbeat
