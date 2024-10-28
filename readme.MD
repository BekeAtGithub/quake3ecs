## Step 1 acquire application
Download this repository and unzip into your repo folder:
https://github.com/treyyoder/quakejs-docker

Build image from directory
docker build --add-host=content.quakejs.com:127.0.0.1 -t treyyoder/quakejs:latest .

Push docker image to AWS ECR
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <account-id>.dkr.ecr.us-east-1.amazonaws.com

Tag Docker Image
docker tag node-app:latest <account-id>.dkr.ecr.us-east-1.amazonaws.com/node-app:latest

Push Docker Image
docker push <account-id>.dkr.ecr.us-east-1.amazonaws.com/node-app:latest

## Step 2 Deployment 

setup Main.tf file with basic infrastructure provisioning to support the containerization of the quake 3 Dockerfile
exposing port 80, 8080, 27960

terraform init

terraform plan

terraform apply

![alt text](https://github.com/BekeAtGithub/flaskEC2/blob/master/FlaskEC2.drawio.png)