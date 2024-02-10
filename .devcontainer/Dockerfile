FROM python:3.11-slim-bookworm

COPY  ./zshrc /home/$USERNAME/.zshrc

RUN apt update && \
    apt upgrade -y

# unzip / less / groff are required for awscli
# gcc required for pythong libraries
RUN apt install curl gcc less groff unzip zsh git make -y

# python libraries
COPY ./requirements.txt /tmp/pip-tmp/requirements.txt
RUN pip install --upgrade pip \
  && pip --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
  && rm -rf /tmp/pip-tmp

# granted/assume
RUN curl -OL releases.commonfate.io/granted/v0.20.6/granted_0.20.6_linux_x86_64.tar.gz
RUN tar -zxvf ./granted_0.20.6_linux_x86_64.tar.gz -C /usr/local/bin/ \
  && rm granted_0.20.6_linux_x86_64.tar.gz

# copy over config for granted/assume
RUN mkdir -p /root/.granted
COPY ./config /root/.granted/config
RUN echo 'alias assume=". assume"' >> /root/.profile

# aws cli
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip" \
  && unzip awscliv2.zip \
  && ./aws/install \
  && rm awscliv2.zip

## install oh-my-zsh
# with robbyrussell" and git/aws plugins
RUN sh -c "$(curl -L  https://github.com/deluan/zsh-in-docker/releases/download/v1.1.5/zsh-in-docker.sh)" -- \
    -t robbyrussell \
    -p git -p aws

# setup granted / assume autocompletion
RUN /usr/local/bin/granted completion -s zsh

# Change default SHELL
RUN chsh -s /usr/bin/zsh && source ~/zshrc

ENV PYTHONBUFFERED=TRUE
ENV DEVCONTAINER=true