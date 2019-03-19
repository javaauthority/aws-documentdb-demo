# aws-documentdb-demo
## Demo repo for AWS DocumentDB

1.  Create a VPC with at least 1 public subnet and at least 2 private subnets (https://console.aws.amazon.com/vpc/home)

2.  Create an EC2 instance and choose the public subnet. 

    *   Download the SSH key. You'll need it to connect to the instance
    *   Take note of the Security Group created for your instance

3.  Create a Security Group for DocumentDB

    * Add an inbound "Custom TCP Rule", Protocol "TCP", Port Range "27017-27019", Source "EC2 Instance S.G." (step 2)

4.  Go to DocumentDB (https://console.aws.amazon.com/docdb/home)

5.  Create a Subnet Group and add the private subnets.

6.  Create a Parameter Group

7.  Click on Clusters, then click on the Create button (far right)

8.  **Configuration:** 

    *   Choose a name (cluster identifier)
    *   Choose your instance class (r4 types) (pricing at https://aws.amazon.com/ec2/pricing/on-demand/)
    *   Choose the number of instances (minimum of three)

9.  **Authentication:**

    *   Choose a Master username
    *   Choose a Master password and confirm it
    
10. Click on Show advanced settings

11.  
