# aws-documentdb-demo
## Demo repo for AWS DocumentDB

1.  Create a VPC with at least 1 public subnet and at least 2 private subnets (https://console.aws.amazon.com/vpc/home)

2.  Create an EC2 instance and choose the public subnet. 

    *   Download the SSH key. You'll need it to connect to the instance.

2.  Go to DocumentDB (https://console.aws.amazon.com/docdb/home)

3.  Create a Subnet Group and add the private subnets.

4.  Create a Parameter Group

5.  Click on Clusters, then click on the Create button (far right)

6.  **Configuration:** 

    *   Choose a name (cluster identifier)
    *   Choose your instance class (r4 types) (pricing at https://aws.amazon.com/ec2/pricing/on-demand/)
    *   Choose the number of instances (minimum of three)

7.  **Authentication:**

    *   Choose a Master username
    *   Choose a Master password and confirm it
    
8.  Click on Show advanced settings

9.  
