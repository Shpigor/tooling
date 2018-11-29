FROM jenkinsci/jenkins:lts

USER root

RUN apt-get update && \
    apt-get -y install apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common && \
    curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
    add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian   stretch     stable" && \
    apt-get update && \
    apt-get -y install docker-ce && \
    apt-get -y install maven

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN rm -rf /var/lib/apt/lists/*

RUN usermod -aG docker jenkins

USER jenkins