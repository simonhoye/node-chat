# Node Chat

A simple chat demo for socket.io

## Build docker image

```
$ docker build -t node-chat .
```

## Push image to container registry

### Login to ECR
```
$ `aws ecr get-login --no-include-email --region <YOUR_REGION>`
```

### Tag image
```
$ docker tag node-chat:latest <YOUR_RESPOSITORY>.dkr.ecr.<YOUR_REGION>.amazonaws.com/node-chat:v1
```

### Push image to repository
```
$ docker push <YOUR_REPOSITORY>.dkr.ecr.<YOUR_REGION>.amazonaws.com/node-chat:v1
```

## Run environemnt locally
```
docker network create node-chat
docker run -d --net=node-chat --name redis redis
docker run -d --net=node-chat --name node-chat1 -p 3000:3000 -e "REDIS_ENDPOINT=redis" node-chat
docker run -d --net=node-chat --name node-chat2 -p 3001:3000 -e "REDIS_ENDPOINT=redis" node-chat
```

And point your browser to `http://localhost:3000`.

## Deploy on AWS FARGATE

### Deploy cluster
```
$ aws cloudformation deploy --stack-name=<STACK_NAME> --template-file=cf/cluster.yml --capabilities=CAPABILITY_IAM --region=<YOUR_REGION>
```

### Deploy resources
```
$ aws cloudformation deploy --stack-name=<STACK_NAME> --template-file=cf/resources.yml --capabilities=CAPABILITY_IAM --region=<YOUR_REGION>
```

### Deploy the chat service
Use Cloud Formation console