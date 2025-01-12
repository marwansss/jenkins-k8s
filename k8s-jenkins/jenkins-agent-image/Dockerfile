# Installing  kubectl and containerd binaries
FROM ubuntu 

RUN apt-get update && apt-get install -y apt-transport-https ca-certificates curl gpg

# Install kubectl using APT
RUN curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.30/deb/Release.key | gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg \
    && echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.30/deb/ /' | tee /etc/apt/sources.list.d/kubernetes.list \
    && apt-get update && apt-get install -y kubectl

# Install containerd using binary download
RUN apt-get update && \
    apt-get install -y curl && \
    curl -LO https://github.com/kubernetes-sigs/cri-tools/releases/download/v1.28.0/crictl-v1.28.0-linux-amd64.tar.gz && \
    mkdir -p /data && \
    tar -zxvf crictl-v1.28.0-linux-amd64.tar.gz -C /usr/local/bin && \
    chmod +x /usr/local/bin/crictl
CMD ["tail", "-f", "/dev/null"]

