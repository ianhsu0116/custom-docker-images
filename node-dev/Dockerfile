FROM public.ecr.aws/aws-cli/aws-cli:2.31.39

USER root

RUN yum update -y && \
    yum install -y \
        docker \
        git \
        tar \
        xz && \
    yum clean all

RUN curl -fsSL https://rpm.nodesource.com/setup_20.x | bash - && \
    yum install -y nodejs && \
    yum clean all

# corepack + Yarn 1
RUN corepack enable && \
    corepack prepare yarn@1.22.22 --activate
