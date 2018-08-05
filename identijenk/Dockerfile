FROM jenkins/jenkins:lts

# Root user to install using apt-get
USER root

# Docker install as the Docker docs 
RUN apt-get update && apt-get -y install \
	apt-transport-https \
	ca-certificates \
	curl \
	gnupg2 \
	software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update && apt-get -y install docker-ce

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

# Docker compose install
RUN sudo curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose \
    && chmod +x /usr/local/bin/docker-compose

# Jenkisn best pratctices
USER jenkins

