FROM alpine:3.8

RUN apk update \
  && apk upgrade \
  && apk add --no-cache \
             rsync \
             openssh-client \
             curl \
             zip \
  && rm -rf /var/cache/apk/*

RUN mkdir -p ~/.ssh \
    && touch ~/.ssh/known_hosts \
    && chmod 700 ~/.ssh \
    && chmod 644 ~/.ssh/known_hosts
