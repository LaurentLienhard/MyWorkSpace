FROM debian:bullseye
LABEL maintainer="Laurent LIENHARD <laurent@lienhard.fr>" \
      description="A Docker image for dev my stuff easily." \
      version="1.0.0"

RUN apt-get update && apt-get install -y
RUN apt-get install python3 python3-dev python3-venv tree python3-pip git direnv make bash curl wget sudo lsb-release software-properties-common xorriso vim sshpass apt-transport-https ca-certificates gpg -y 

# Install terraform / packer / vagrant
RUN wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list && \
    apt-get update && apt-get install terraform packer vagrant -y

# Install terraform-docs
RUN wget https://github.com/terraform-docs/terraform-docs/releases/download/v0.16.0/terraform-docs-v0.16.0-linux-amd64.tar.gz && \
    tar -xvf terraform-docs-v0.16.0-linux-amd64.tar.gz && \
    mv terraform-docs /usr/local/bin/

