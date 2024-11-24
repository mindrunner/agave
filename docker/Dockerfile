FROM ubuntu:24.04

ARG agave_version=2.0.16
ENV AGAVE_VERSION=${agave_version}
ENV PATH="/home/agave/.local/share/solana/install/active_release/bin:$PATH"

RUN apt-get update && apt-get install -y \
  bash \
  bzip2 \
  curl \
  iproute2 \
  jq \
  openssl \
  tzdata \
  vim && \
  userdel ubuntu && \
  useradd -ms /bin/bash agave

USER agave

WORKDIR /home/agave

ADD --chmod=0755 https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh /usr/local/bin/

COPY --chown=agave:agave --chmod=0755 bin/* /usr/local/bin/

RUN sh -c "$(curl -sSfL https://release.anza.xyz/v${agave_version}/install)"
