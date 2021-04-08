# Udagram

## Description

In this project, a web app with high availability is deployed to AWS using Cloudformation.

In this scenario, we are deploying an Apache Web Server and grabbing the JavaScript and HTML files from an S3 bucket.

## Commands

### Cloudformation

To create the network CloudFormation stack:

```sh
$ aws cloudformation create-stack --stack-name udagram-network --template-body file://network.yml  --parameters file://network-params.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1 --profile devops
```

To update the network CloudFormation stack:

```sh
$ aws cloudformation update-stack --stack-name udagram-network --template-body file://network.yml  --parameters file://network-params.json --region=us-east-1 --profile devops
```

To create the servers CloudFormation stack:

```sh
$ aws cloudformation create-stack --stack-name udagram-servers --template-body file://infrastructure/servers/servers.yml  --parameters file://infrastructure/servers/servers-params.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1 --profile devops
```

To update the servers CloudFormation stack:

```sh
$ aws cloudformation update-stack --stack-name udagram-servers --template-body file://infrastructure/servers/servers.yml  --parameters file://infrastructure/servers/servers-params.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1 --profile devops
```

### S3

To upload files from a local directory to an S3 bucket named `026581830011-udagram-code`

```sh
$ aws s3 cp --recursive ./src s3://026581830011-udagram-code --profile devops
```

To download files from an S3 bucket folder to a local directory:

```sh
$ aws s3 cp --recursive s3://026581830011-udagram-code/ /var/www/html
```