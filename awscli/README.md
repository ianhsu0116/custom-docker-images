# AWSCLI

> This is a special image for building other docker images for gitlab runner. It can not be pulled by gitlab runner before running `aws ecr login` command. So I make this image public and build it manually.

##### Set docker registry
```bash
export ECR_PUB_REG='public.ecr.aws/n1l6j6z8'
export AWSCLI_REPO='ian/awscli'
```

##### build image
```bash
cd awscli
docker image build -t ${ECR_PUB_REG}/${AWSCLI_REPO}:2.31.39 .
```

##### login ECS Public Registry
```bash
aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/o7d5n1x9
```

##### push image
```bash
docker image push ${ECR_PUB_REG}/${AWSCLI_REPO}:2.31.39
```

##### Unset docker registry
```bash
unset ECR_PUB_REG
unset AWSCLI_REPO
```