FROM ubuntu:trusty
# Dockerfile to run Syncthing. Requires an external container manager such as systemd to auto-restart the container when Syncthing restarts.
MAINTAINER Scott Hansen <firecat4153@gmail.com>

ENV SYNCTHING_USER syncthing
ENV UID 22000

RUN apt-get update && apt-get install -qy supervisor ca-certificates
RUN useradd --no-create-home -g users --uid $UID $SYNCTHING_USER
ADD https://github.com/syncthing/syncthing/releases/download/v0.11.17/syncthing-linux-amd64-v0.11.17.tar.gz /syncthing.tar.gz
RUN tar -xzvf syncthing.tar.gz && mv sync*/syncthing /syncthing && rm syncthing.tar.gz
# To use an existing syncthing binary in the root directory, comment out the previous 2 lines and uncomment the next line.
# COPY syncthing /syncthing

USER $SYNCTHING_USER

CMD ["/syncthing", "-home=/config"]
