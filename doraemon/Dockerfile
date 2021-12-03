#
# doraemon
#
# build:
#   docker build --force-rm -t doraemon .
# run:
#   docker run --rm -it --name doraemon doraemon
#

FROM debian:stretch-slim
LABEL maintainer="Byungjin Park <posquit0.b@gmail.com>"
LABEL description="All-in-one box to test and debug the infrstructure."

# Install needed packages
RUN \
  apt update \
  && apt install -y wget curl iputils-arping iputils-ping dnsutils traceroute tcpdump telnet nmap \
  && apt install -y openssh-client git \
  && apt install -y busybox tar unzip less jq tree vim \
  && rm -rf /var/lib/apt/lists/*

# Install aws-cli v2
RUN \
  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
  && unzip awscliv2.zip \
  && ./aws/install \
  && rm -rf ./aws \
  && rm -f ./awscliv2.zip

# Download executable binaries
RUN \
  (wget https://github.com/fullstorydev/grpcurl/releases/download/v1.8.1/grpcurl_1.8.1_linux_x86_64.tar.gz -c -O - | tar -xvz grpcurl) \
  && mv grpcurl /usr/local/bin/ \
  && chmod -R ug+x /usr/local/bin

# Run forever
CMD tail -f /dev/null
