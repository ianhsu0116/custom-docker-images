ARG AWSCLI_VER

FROM public.ecr.aws/aws-cli/aws-cli:${AWSCLI_VER}

USER root

RUN yum update -y && \
    yum install -y \
        docker \
        git \
        tar \
        xz && \
    yum clean all

ARG NODE_MAJOR

RUN curl -fsSL https://rpm.nodesource.com/setup_${NODE_MAJOR}.x | bash - && \
    yum install -y nodejs && \
    yum clean all

# corepack + Yarn 1
RUN corepack enable && \
    corepack prepare yarn@1.22.22 --activate
