# learn_aws
learning aws through projects


## AWS commands to set up in local
- brew install awscli
- aws configure
    - get the access key and secret from security credentials in aws website.


## s3 buckets
- aws s3 ls
- creating bucket
    - aws s3 mb s3://ashok-firstbucket-cli --region us-east-1
- syncing current directory files to aws bucket online
    - aws s3 sync . s3://ashok-firstbucket-cli
- syncing aws online to current directory (copy all files from s3 bucket to local current direc)
    - aws s3 synch s3://ashok-firstbucket-cli .
- Copy file
    - aws s3 cp ./Satya_D_Resume.pdf s3://ashok-firstbucket-cli


# EKSCTL
- install eksctl (google it ) in macos
    - brew install eksctl
- eksctl is a tool to create eks cluster (kubernetes cluster) on AWS. Alternatively, one can use cloud formation to create eks cluster but it's a lot of steps. EKSCTL abstracts all that.
- eksctl version
- install kubectl for macos
    - brew install kubernetes-cli
- kubectl version --client
- create eks cluster with free tier
    - eksctl create cluster --node-type t3.medium --nodes 2
    - it creates bunch of stuff like vpc, route table, eks cluter.
- information on clusters in aws
    - eksctl get cluster  
- ec2 instances which have been provisioned and up for this cluster
    - kubectl get nodes
- Can access the same in Elastic Kubernetes service in AWS website.
- deploy pods replicas , service everthing written inside a single .yaml file
    - kubectl apply -f <file.yaml>
- get all running pods (deployments, service, etc)
    - kubectl get all
- 
