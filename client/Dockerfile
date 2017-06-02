FROM ubuntu

ENV CONSUL_VERSION=0.8.3

RUN apt-get update && \
  apt-get install -y wget unzip && \
  apt-get clean

RUN wget https://releases.hashicorp.com/consul/0.8.3/consul_${CONSUL_VERSION}_linux_amd64.zip && \
  unzip consul_${CONSUL_VERSION}_linux_amd64.zip && \
  rm consul_${CONSUL_VERSION}_linux_amd64.zip

RUN mv ./consul /usr/bin/consul

RUN mkdir -p /consul/data && \
  mkdir -p /consul/config

EXPOSE 8300
EXPOSE 8301 8301/udp 8302 8302/udp
EXPOSE 8500

ENTRYPOINT ["consul"]

CMD ["agent", "-data-dir=/consul/data", "-disable-host-node-id", "-bind=0.0.0.0", "-client=0.0.0.0", "-join=172.17.0.2" ]
