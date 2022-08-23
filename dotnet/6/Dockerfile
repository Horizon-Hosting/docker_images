# ----------------------------------
# Pterodactyl .NET Core 6.0 Pterodactyl Image DockerFile
# Environment: Linux
# ----------------------------------
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base

MAINTAINER Hayden X, <hayden@horizonnetworks.uk>

RUN apt update
RUN apt install -y curl ca-certificates openssl git tar zip unzip bash fontconfig wget
RUN apt install -y dos2unix
RUN apt install -y sqlite3 libsqlite3-dev libmariadb-dev
RUN apt install -y locales
RUN dpkg-reconfigure --frontend noninteractive locales
RUN useradd -m -d /home/container -s /bin/bash container
                
RUN apt -y install dos2unix

COPY ./entrypoint.sh entrypoint.sh
COPY ./entrypoint.sh /home/container/entrypoint.sh

RUN dos2unix entrypoint.sh
RUN dos2unix /home/container/entrypoint.sh
RUN chmod +x /home/container/entrypoint.sh
RUN chmod +x entrypoint.sh

#ENV         DEBIAN_FRONTEND noninteractive

WORKDIR /home/container

USER container
ENV  USER=container HOME=/home/container


ENTRYPOINT ["/entrypoint.sh"]