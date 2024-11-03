FROM ubuntu:24.04

# Add Docker's official GPG key:
RUN apt-get update -qq 
RUN apt-get install -qqy ca-certificates curl
RUN install -m 0755 -d /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
RUN chmod a+r /etc/apt/keyrings/docker.asc
    
# Add the repository to Apt sources:
RUN echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
      $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
      tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get update -qq 
RUN apt-get install -qqy docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin 

# Install the magic wrapper.
ADD ./wrapdocker.sh /usr/local/bin/wrapdocker.sh
RUN chmod +x /usr/local/bin/wrapdocker.sh

# Define additional metadata for our image.
VOLUME /var/lib/docker
CMD ["wrapdocker.sh"]