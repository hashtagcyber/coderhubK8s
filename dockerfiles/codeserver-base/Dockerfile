FROM codercom/code-server:4.19.1

# Install Docker CLI
USER root
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
$(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

RUN apt-get update && apt-get install -y docker-ce-cli

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

USER coder
# Set the entrypoint to be used with JupyterHub
ENTRYPOINT ["/usr/bin/code-server","--bind-addr","0.0.0.0:8888",".", "--auth","none","--disable-telemetry","--ignore-last-opened", "-vvv"]