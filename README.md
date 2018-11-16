# Node Chat

A simple chat demo for socket.io

## Build docker image

```
$ docker build -t node-chat .
```

## Run docker image
```
$ docker run -d --name node-chat -p 3000:3000 node-chat
```

And point your browser to `http://localhost:3000`.

## Deploy on AWS FARGATE

```
$ aws cloudformation deploy --stack-name=production --template-file=cf/public-vpc.yml --capabilities=CAPABILITY_IAM --region=<YOUR_REGION>
```
