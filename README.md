# darwin-tasks
#PYTHON-TAKS

$ Launch instance
$ install docker and start the docker 
$  create a docker file for python and nginx-passenger
$  build the docker image
      
      + docker build -t <image-name> <path-to-file>
      
$ create docker container by using  created docker image
      
      + docker run -d -p assignport:defaultport  <image name/id>
      
$ check application working or not with public IP of instance
$ In, AWS console create ECR container
$  Retrieve an authentication token and authenticate your Docker client to your registry.
Use the AWS CLI:
       
       + aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin <AWS-account-id>.dkr.ecr.us-east-2.amazonaws.com
    
$  After the build is completed, tag your image so you can push the image to this repository:
       
       + docker tag <image-name:latest> <AWS-acount-id>.dkr.ecr.us-east-2.amazonaws.com/<images-name>:latest
$ Run the following command to push this image to your newly created AWS repository:
       
       +  docker push <AWS-account-id>.dkr.ecr.us-east-2.amazonaws.com/<image-name>:latest

$ it successfully pushed into ECR 



# DEPLOY PHP-APPLICATION BY USING KUBERNETES

$ launch instance

$  install docke and start the docker

$  create a Dockerfile for php-mongodb application

$  build the docker images 
        
        + docker build -t <image-name> <path-to-file>

$  create docker container by using created docker image
        
        + docker run -d -p assignport:defaultport  <image name/id>

$ check application working or not with public IP of instance

$ In, AWS console create ECR container

$  Retrieve an authentication token and authenticate your Docker client to your registry.
Use the AWS CLI:
       
       + aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin <AWS-account-id>.dkr.ecr.us-east-2.amazonaws.com
    
$  After the build is completed, tag your image so you can push the image to this repository:
       
       + docker tag <image-name:latest> <AWS-acount-id>.dkr.ecr.us-east-2.amazonaws.com/<images-name>:latest

$ Run the following command to push this image to your newly created AWS repository:
       
       +  docker push <AWS-account-id>.dkr.ecr.us-east-2.amazonaws.com/<image-name>:latest

$ it successfully pushed into ECR 


$ install aws cli
        
        + https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
$ install kops 
        
        + https://kubernetes.io/docs/setup/production-environment/tools/kops/
$ install kubectl
        
        + https://pwittrock.github.io/docs/tasks/tools/install-kubectl/
$ create s3 bucket 
       
       + aws s3 mb s3://<name>
$ export that s3 bucket by using below command
       
       + export KOPS_STATE_STORE=s3://<name>
$ create a cluster with two nodes
       
       + kops create cluster --name=<cluster-name> --state=<s3bucket-name> --node-count=2 --yes
$ for getting nodes use below command
       
       + kubectl get nodes

$ wirte deployment file and service for our create php-mongodb image 

$ write autoscaling file with metrics

$ apply these three file by using
       
       + kubectl apply -f <file-name>
$ To get all details use below command
       
       + kubectl get all
$ check application working or not with Loadbalancer DNS


$ create Route 53 private hosted zone 
$ In, this zone create Record with CNAME 
$ copy the "ns-values" and paste those into your domain name 
$ save it
$ if you want browse the application with your Domain name please wait 48 hours(I don't exactly)
  
      
# CREATE EKS CLUSTER BY USING TERRAFORM
      
 $ launch instance
 $ install terraform 
 $ create a directory
 $ create provider.tf file 
 $ create vpc.tf
 $ create security.tf
 $ create eks.tf file
 $ inititlize the directory
      
      + terraform init
 $ To generates a detailed report that lists all the resources that will be created, modified, or destroyed in order to achieve the desired state by using below command
      
      + terraform plan
 $ creating resources by using below command
      
      + terraform apply --auto-approve

