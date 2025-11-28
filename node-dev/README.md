# AWSCLI

> This is a special image for building other docker images for gitlab runner. It can not be pulled by gitlab runner before running `aws ecr login` command. So I make this image public and build it manually.

##### Set docker registry
```bash
cd node-dev
export ECR_PUB_REG='public.ecr.aws/n1l6j6z8'
export AWSCLI_REPO='node-dev'
export IMAGE_TAG=$(cat VERSION)
export BUILD_ARGS=$(sed 's/^/--build-arg /g' ./ARGS | tr '\n' ' ')
```

##### login ECS Private Registry
```bash
aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 948608138159.dkr.ecr.us-west-2.amazonaws.com
```

##### login ECS Public Registry
```bash
aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/n1l6j6z8
```

##### build image
```bash
docker image build \
  --platform=linux/amd64 \
  -t ${ECR_PUB_REG}/${AWSCLI_REPO}:${IMAGE_TAG} \
  --build-arg=NODE_VER=20.x \
  .
```

##### push image
```bash
docker image push ${ECR_PUB_REG}/${AWSCLI_REPO}:${IMAGE_TAG}
```

##### Unset docker registry
```bash
unset ECR_PUB_REG
unset AWSCLI_REPO
unset IMAGE_TAG
unset BUILD_ARGS
```