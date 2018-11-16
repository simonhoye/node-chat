# Node Chat

A simple chat demo for socket.io

## Build docker image

```
$ docker build -t node-chat .
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

```
$ aws cloudformation deploy --stack-name=production --template-file=cf/public-vpc.yml --capabilities=CAPABILITY_IAM --region=<YOUR_REGION>
```
