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

