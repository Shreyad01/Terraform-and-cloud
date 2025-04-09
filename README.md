# Terraform ECS Fargate Infrastructure on AWS

This project provisions a complete server-based infrastructure on AWS using **Terraform**. It deploys a containerized application to **AWS ECS Fargate** behind a **Load Balancer**, within a secure **VPC** network.

## Key Components Included:

- **VPC** with:
  - 2 Public Subnets
  - 2 Private Subnets
  - Internet Gateway (for public access)
  - NAT Gateway (for outbound internet access from private subnets)
- **Security Groups** for ECS and Load Balancer
- **ECS Cluster** (Fargate Launch Type)
- **ECS Task Definition** and **Service**
  - Runs container in **private subnets**
- **Application Load Balancer**
  - In public subnets
  - Forwards traffic to ECS service in private subnets

## Steps 
- create terraform.tf file and Outputs.tf file
- write code in terraform.tf file and output.tf file 

    [terraform.tf](terraform.tf)

    [output.tf](outputs.tf)

- verify AWS CLI installed using :

      aws --version

![alt text](<images/aws version.png>)

- check aws configuration using :

      aws configure list

- It will show :
     
      profile

      access_key

      secret_key

      region

- Initialize the Terraform using :
    
      terraform init

![alt text](<images/terraform init.png>)

- Validate the configuration using :

      terraform validate

![alt text](<images/terraform validate.png>)

- Review the plan using :
  
      terraform plan

![alt text](<images/terraform plan.png>)

- Apply the plan using :

      terraform apply

![alt text](<images/terraform apply.png>)

![alt text](<images/terraform apply 2.png>)

- To monitor Deployment 
  
  1) Go to AWS Console → ECS → View your cluster & service

      ![alt text](images/ECS.png)

  2) Go to EC2 → Load Balancers → Check DNS name

      ![alt text](<images/load balancer.png>)

  3) Go to VPC to verify subnets, NAT, etc.
     
      ![alt text](images/VPC.png)

- Access the Application using browser
  
      http://<alb-dns-name>

![alt text](<images/final result.png>)
