ARG REGISTRY
FROM $REGISTRY/debian:buster-slim
RUN apt-get update && apt-get -y install --no-install-recommends \
    cgit \
    fcgiwrap \
    dumb-init \
    && rm -rf /var/lib/apt/lists/*
COPY cgitrc /etc/cgitrc
RUN useradd --home /var/lib/git --shell /bin/false git
USER git
EXPOSE 9000/tcp
CMD ["dumb-init", "--", "spawn-fcgi", "-p", "9000", "-n", "--", "/usr/sbin/fcgiwrap"]
