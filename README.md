# learn_aws
learning aws through projects


## AWS commands to set up in local
- `brew install awscli`
- `aws configure`
    - get the access key and secret from security credentials in aws website.


## s3 buckets
- `aws s3 ls`
- creating bucket
    - `aws s3 mb s3://ashok-firstbucket-cli --region us-east-1`
- syncing current directory files to aws bucket online
    - `aws s3 sync . s3://ashok-firstbucket-cli`
- syncing aws online to current directory (copy all files from s3 bucket to local current direc)
    - `aws s3 synch s3://ashok-firstbucket-cli .`
- Copy file
    - `aws s3 cp ./Satya_D_Resume.pdf s3://ashok-firstbucket-cli`


# EKSCTL
- install eksctl (google it ) in macos
    - `brew install eksctl`
- eksctl is a tool to create eks cluster (kubernetes cluster) on AWS. Alternatively, one can use cloud formation to create eks cluster but it's a lot of steps. EKSCTL abstracts all that.
- `eksctl version`
- install kubectl for macos
    - `brew install kubernetes-cli`
- `kubectl version --client`
- create eks cluster with free tier
    - `eksctl create cluster --node-type t3.medium --nodes 2`
    - it creates bunch of stuff like vpc, route table, eks cluter.
- information on clusters in aws
    - `eksctl get cluster`
- ec2 instances which have been provisioned and up for this cluster
    - `kubectl get nodes`
- Can access the same in Elastic Kubernetes service in AWS website.
- deploy pods replicas , service everthing written inside a single .yaml file
    - `kubectl apply -f <file.yaml>`
- get all running pods (deployments, service, etc)
    - `kubectl get all`
- access a pod from terminal
    - `kubectl exec -it <pod_name> -- /bin/sh`
    - this is like an OS since each pod is a separate operating system.
- update and install packages in this pod's OS
    - `apt-get update`
    - `apt-get install vim nano` installs both vim and nano editors
- delete service, deployments
    - `kubectl delete deployment <deployment_name>`
    - `kubectl delete service <service_name>`

# Docker
- If I have a docker file, I want to create an image and publish it to docker hub so that I can pull that image whereever I want and run as a container.
    - `docker build -t <to_be_generated_container_image_name> .` to run the Docker file in the current directory and to create the container along with all the artifacts (dependent files). `.` means all the artifacts necessary will be in the current directory.
- `docker images` to see the generated image and other images.
- Run the docker container image named: custom-httpd
    - `docker run -d -p 8080:80 custom-httpd` d is to run on Daemon mode so it doesn't take over entire command line. Exposing port 80 of the container to the local host port 8080. It means we forwarded container's port 80 to local port 8080.
- `docker ps` to see which containers are running in the local
-  `docker stop <container id>` to stop the container.
- Pushing an image to docker hub
    - Create a new repository in docker hub after logging in with credentials.
    - Need to first tag the image and then execute the push command
    - from cli, login to remote docker hub `docker login --username=<user_name>`
    - Tag the image with docker hub repository `docker tag <Image_id> <username>/<repositoryname>:<optional_new_tag_name>`
    - `docker images` contains our newly tagged image.
    - pushing that tagged image which is present in local machine to docker hub `docker push <image_name>`


# AWS Knowledge
- Elastic Bean stalk takes care of auto-scaling, managing the web servers, etc..
- S3 bucket is created with you provision elastic bean stalk application. It creates S3 bucket to save your code, log files, etc. 
- AWS CloudFormation is an Infrastructure as code (IaC) service that enables you to model, provision, and manage AWs and third-party resources using declarative templates written in yaml or json. Instead of manually configuring AWS resources through the console, you define your entire infrastructre such as EC2 instances, S3 buckets, databases, and load balancers in a template file. Cloud Formation then automatically provisions and configures these resources in a predictable, repeatable and safe manner.
- 