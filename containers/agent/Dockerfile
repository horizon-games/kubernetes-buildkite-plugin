ARG BUILDKITE_AGENT_VERSION="latest"
ARG KUBERNETES_VERSION="v1.24.11"

FROM buildkite/agent:${BUILDKITE_AGENT_VERSION}

ARG BUILDKITE_AGENT_VERSION
ARG KUBERNETES_VERSION
ARG CI_COMMIT_TIMESTAMP
ARG CI_COMMIT_SHA
ARG CI_COMMIT_TAG

USER root

COPY entrypoint.sh /entrypoint.sh

RUN apk add --no-cache bash ca-certificates coreutils curl git jq libstdc++ openssh jsonnet openssh-client-default
RUN curl -sfL https://storage.googleapis.com/kubernetes-release/release/${KUBERNETES_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl \
    && chmod +x /usr/local/bin/kubectl

ENTRYPOINT [ "/entrypoint.sh"]
CMD ["start"]
