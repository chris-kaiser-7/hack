FROM debian:bookworm

RUN apt-get update && apt-get install -y ca-certificates curl

RUN install -m 0755 -d /etc/apt/keyrings

RUN curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc \
  && chmod a+r /etc/apt/keyrings/docker.asc

RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null

RUN apt-get update && apt-get install -y docker-ce docker-ce-cli docker-ce-rootless-extras containerd.io docker-buildx-plugin

RUN apt-get install -y uidmap dbus-user-session fuse-overlayfs slirp4netns

RUN rm -rf /var/lib/apt/lists/*

RUN useradd -ms /bin/bash appuser
WORKDIR /home/appuser
USER appuser

#RUN dockerd-rootless-setuptool.sh install

ENTRYPOINT ["bash"]


# ENV KIND_VERSION=v0.23.0
# RUN [ $(uname -m) = x86_64 ] && curl -Lo /usr/local/bin/kind https://kind.sigs.k8s.io/dl/${KIND_VERSION}/kind-linux-amd64 \
#   && chmod +x /usr/local/bin/kind
# RUN kind --version
#
# RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
# RUN install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
# RUN kubectl version --client
#
#
# CMD ["tail", "-f", "/dev/null"]




################################
################################
################################
# RUN [ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.29.0/kind-linux-amd64
# RUN chmod +x ./kind
# RUN mv ./kind /usr/local/bin/kind

# Install kind
# ENV KIND_VERSION=v0.23.0
# RUN curl -Lo /usr/local/bin/kind https://kind.sigs.k8s.io/dl/${KIND_VERSION}/kind-linux-amd64 \
#     && chmod +x /usr/local/bin/kind

# Install kubectl
# ENV KUBECTL_VERSION=v1.29.0
# RUN curl -LO "https://dl.k8s.io/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl" \
#     && chmod +x kubectl \
#     && mv kubectl /usr/local/bin/
