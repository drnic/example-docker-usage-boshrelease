# VERSION 0.1
# DOCKER-VERSION  0.7.3
# AUTHOR:         Dr Nic Williams <drnicwilliams@gmail.com>
# DESCRIPTION:    Redis server (2.8.5)
# TO_BUILD:       docker build -t redis .
# TO_RUN:         docker run -p 6379:6379 -v path/to/store:/store redis

FROM ubuntu:13.04

RUN apt-get update
RUN apt-get install -y build-essential

ADD redis-2.8.5.tar.gz /tmp/redis/

RUN cd /tmp/redis/redis-2.8.5 ;\
    make install

