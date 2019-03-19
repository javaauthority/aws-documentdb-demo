# Repository for the AWS DocumentDB Demo


## 01. [VPC Setup](01_vpc_setup/vpcsetup.md)

1.  Create a VPC with at least 1 public subnet and at least 2 private subnets (https://console.aws.amazon.com/vpc/home)

2.  Create an EC2 instance to serve as a JumpBox and choose the public subnet. 

    *   Download the SSH key. You'll need it to connect to the instance
    *   Take note of the Security Group created for your instance

3.  Create a Security Group for DocumentDB

    * Add an Inbound "Custom TCP Rule" 
         *  Protocol: TCP 
         *  Port Range: 27017-27019 
         *  Source: EC2 Instance Security Group (see Step 2)

## 02. [DocumentDB Setup](02_documentdb_setup/documentdbsetup.md)

4.  Go to DocumentDB (https://console.aws.amazon.com/docdb/home)

5.  Create a Subnet Group and add the private subnets.

6.  Create a Parameter Group

7.  Click on Clusters, then click on the Create button (far right)

8.  **Configuration:** 

    * Choose a name (cluster identifier)
    * Choose your instance class (r4 types) (pricing at https://aws.amazon.com/ec2/pricing/on-demand/)
    * Choose the number of instances (minimum of three)

9.  **Authentication:**

    * Choose a Master username
    * Choose a Master password and confirm it
    
10. Click on Show advanced settings

11. **Network Settings:**

    * Choose your VPC
    * Choose the Subnet Group you defined in Step 5
    * Choose the Security Group you defined in Step 3

12. **Cluster Options:**
    
    * Choose the Parameter Group you defined in Step 6
    
13. **Encryption-at-rest:**
    
    * Enable it and choose the KMS Key
    
14. **Backup:**

    * Choose your backup retention period and backup window
    
15. **Log Exports:**

    * Enable it if needed
    
16. **Maintenance:**

    * Select your maintenance window
    
17. Click on the Create Cluster button

18. Wait for your cluster to be created... count to 100. If not created, repeat.

19. Take note of the **Connect** settings. You'll need them soon.


## [Connecting to your DocumentDB cluster]()

20. Make sure your EC2 instance (Step 2) is running

21. Create an SSH Tunnel to your EC2 instance

    * ssh -i /Users/you/.ssh/YOUR_PVT_KEY -L 27017:HOST_NAME:27017 ec2-user@EC2_INSTANCE_IP_ADDRESS -N

22. Download the AWS RDS' key (https://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.pem)

23. If using Java, do the following:

    * Add the AWS RDS key to your java keystore
      * cd $JAVA_HOME/jre/lib/security
      * sudo keytool -importcert -trustcacerts -file /path/to/rds-combined-ca-bundle.pem -keystore cacerts
      * default pwd is changeit
      
      * Sample Java code:
        * ```MongoCredential mongoCredential = MongoCredential.createScramSha1Credential(USERNAME, "test", PASSWORD.toCharArray()); 
        credentials.add(mongoCredential);```
        * ```MongoClientOptions mongoClientOptions = MongoClientOptions.builder().sslInvalidHostNameAllowed(true).sslEnabled(true).build();``` 
        * ```ServerAddress serverAddress = new ServerAddress("localhost"); ```
        * ```mongoClient = new MongoClient(serverAddress, credentials, mongoClientOptions);```

24. Install MongoDB via brew (https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)

    * This will give you access to the Mongo Shell

25. Connect to the DocumentDB using the MongoDB shell

    *  mongo --sslAllowInvalidHostnames --ssl --sslCAFile /path/to/rds-combined-ca-bundle.pem --username USER_NAME --password PWD
    
26. Issue a few commands

    * use demo
    * db.aws.insert({"firstName":"Peter","lastName":"Umbridge"})
    * db.local.insert({"firstName":"Greg","lastName":"Pastorelli"})
    * db.aws.find()
    * db.aws.insert({"firstName":"Janet","lastName":"Tridd"})
    * db.aws.find()
    
27. TEAR DOWN YOUR CLUSTER!!!

    * Go to Instances
    * Choose whether or not you want to create a final snapshot
    * Click the checkbox Acknowledgement that you want to delete the cluster
    * Type "delete entire cluster"
