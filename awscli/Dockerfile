ARG AWSCLI_VER

FROM public.ecr.aws/aws-cli/aws-cli:${AWSCLI_VER}

USER root

RUN yum update -y && \
    yum install -y jq tar gzip && \
    yum install -y docker && \
    yum clean all
