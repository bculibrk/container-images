FROM ghcr.io/jrottenberg/ffmpeg:8.1-ubuntu

# Install AWS CLI v2
RUN apt-get -qq -y update && apt-get install -qq -y --no-install-recommends -y \
    curl \
    unzip \
    ca-certificates \
    && curl -s "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip -qq awscliv2.zip \
    && ./aws/install -i /usr/local/aws-cli -b /usr/local/bin \
    && rm -rf awscliv2.zip aws \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN /usr/local/bin/aws --version

# Clear entrypoints and commands to allow for custom execution
ENTRYPOINT [""]
CMD [""]
