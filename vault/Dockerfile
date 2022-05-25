FROM ubuntu:22.04 as build

RUN apt update \
 && apt install -y --no-install-recommends \
      ca-certificates \
      gnupg \
      curl \
      software-properties-common \
 && curl -fsSL "https://apt.releases.hashicorp.com/gpg" | apt-key add - \
 && apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" \
 && apt update \
 && apt install vault \
 && apt clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir /vault

COPY "./config/" "/vault/config/"

EXPOSE 8200

ENTRYPOINT ["vault"]
