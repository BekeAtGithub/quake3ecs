## Step 1 acquire application
Download this repository and unzip into your repo folder:
https://github.com/treyyoder/quakejs-docker

Build image from directory with command:

# docker build --add-host=content.quakejs.com:127.0.0.1 -t treyyoder/quakejs:latest .

Push docker image to AWS ECR with command: # replace region with yours and replace <account-id> with your AWS account id - leave --username as AWS, just leave it 

# aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com  

Tag Docker Image with command:

# docker tag node-app:latest <account-id>.dkr.ecr.<region>.amazonaws.com/node-app:latest

Push Docker Image with command: 

# docker push <account-id>.dkr.ecr.<region>.amazonaws.com/node-app:latest

## Step 2 Deployment - make sure you go through the main.tf file and change the us-east-1 to YOUR region

setup Main.tf file with basic infrastructure provisioning to support the containerization of the quake 3 Dockerfile
exposing port 80, 8080, 27960

terraform init

terraform plan

terraform apply

