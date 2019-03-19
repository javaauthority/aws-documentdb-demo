## 02. DocumentDB Setup

4.  Go to DocumentDB (https://console.aws.amazon.com/docdb/home)

    ![Image of DocumentDB](documentdb.png)

5.  Create a Subnet Group and add the private subnets.

    ![Image of DocumentDB - Create Subnet Group](subnetgroup.png)

6.  Create a Parameter Group

    ![Image of DocumentDB - Create Parameter Group](parametergroup.png)

7.  Click on Clusters, then click on the Create button (far right)

    ![Image of DocumentDB - Create Cluster](createcluster.png)

8.  **Configuration:** 

    * Choose a name (cluster identifier)
    * Choose your instance class (r4 types) (pricing at https://aws.amazon.com/ec2/pricing/on-demand/)
    * Choose the number of instances (minimum of three)

    ![Image of Create Cluster - Configuration](configuration.png)

9.  **Authentication:**

    * Choose a Master username
    * Choose a Master password and confirm it
    
    ![Image of Create Cluster - Authentication](authentication.png)
    
10. Click on Show Advanced Settings

    ![Image of Create Cluster - Show Advanced Settings](advancedsettings.png)

11. **Network Settings:**

    * Choose your VPC
    * Choose the Subnet Group you defined in Step 5
    * Choose the Security Group you defined in Step 3
    
    ![Image of Create Cluster - Network Settings](networksettings.png)

12. **Cluster Options:**
    
    * Choose the Parameter Group you defined in Step 6
    
    ![Image of Create Cluster - Cluster Options](clusteroptions.png)
    
13. **Encryption-at-rest:**
    
    * Enable it and choose the KMS Key
    
    ![Image of Create Cluster - Encryption-At-Rest](encryption.png)
    
14. **Backup:**

    * Choose your backup retention period and backup window
    
    ![Image of Create Cluster - Backup](backup.png)
    
15. **Log Exports:**

    * Enable it if needed
    
    ![Image of Create Cluster - Log Exports](logexports.png)
    
16. **Maintenance:**

    * Select your maintenance window
    
    ![Image of Create Cluster - Maintenance](maintenance.png)
    
17. Click on the Create Cluster button

    ![Image of Create Cluster - Create Cluster](createcluster_end.png)

18. Wait for your cluster to be created... count to 100. If not created, repeat.

    ![Image of Create Cluster - Waiting...](waiting.png)

19. Take note of the **Connect** settings. You'll need them soon.

    ![Image of Create Cluster - Connect](connect.png)
