FROM public.ecr.aws/aws-cli/aws-cli:2.31.39

USER root

RUN yum update -y && \
    yum install -y jq && \
    yum clean all
