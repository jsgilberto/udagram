# Udagram

## Description

In this project, a web app with high availability is deployed to AWS using Cloudformation.

In this scenario, we are deploying an Apache Web Server and grabbing the JavaScript and HTML files from an S3 bucket.

## Commands

To create the network CloudFormation stack:
```sh
aws cloudformation create-stack --stack-name udagram-network --template-body file://network.yml  --parameters file://network-params.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1 --profile devops
```

To update the network CloudFormation stack:
```sh
aws cloudformation update-stack --stack-name udagram-network --template-body file://network.yml  --parameters file://network-params.json --region=us-east-1 --profile devops
```

To create the servers CloudFormation stack:
```sh
aws cloudformation create-stack --stack-name udagram-servers --template-body file://servers.yml  --parameters file://servers-params.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1 --profile devops
```

To update the servers CloudFormation stack:
```sh
aws cloudformation update-stack --stack-name udagram-servers --template-body file://servers.yml  --parameters file://servers-params.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1 --profile devops
```