3-Tier Java Application in AWS


![3-Tier AWS Architecture (1)](https://github.com/user-attachments/assets/61203ba3-a9ff-453e-a8ab-9a878c8c25d9)


A 3-Tier Web Application architecture is a client-server architecture that divides the Java application into three tiers. These three tiers are presentation, application, and database.

1. Presentation tier handles the user interface (Components used EC2 instances, EC2 scaling groups, ALB, IGW, SG's, NAT, IAM, Cloudwatch, Pagerduty)

2. Application tier handles the business logic and processing (Components used EC2 instances, EC2 scaling groups, SG's, IAM), Cloudwatch, Pagerduty

3. Database tier handles data storage,retrieval & replication (Components used AWS RDS, IAM, SG's Cloudwatch, Pagerduty)


The architecture includes several key AWS components to ensure high availability, reliability, scalability, and security. These components include:

- AWS WAF (Web Application Firewall): a managed service that provides an additional layer of protection for web applications by filtering and monitoring HTTP requests to protect against common web exploits and attacks. The WAF is configured with 10 OWASP rules which also include DDos protection, SQL injection etc.

- CloudFront: a content delivery network (CDN) service that caches and distributes static and dynamic content to edge locations around the world, reducing latency and improving performance for end-users.

- Multi-Availability Zone (AZ) deployment: replicating the application across different availability zones to ensure high availability and fault tolerance.

- EC2 Auto Scaling: automatically increasing or decreasing the number of instances to handle large amount of traffic when the need arises. 

- NAT Gateway: providing a managed network address translation (NAT) service to enable instances in private subnets to access the internet or other AWS services while keeping them isolated from the public internet.

- VPC: The VPC & subnets are created within a Multi AZ's region with VPC flow logs enabled to keep track of IP traffic going to and from network interfaces in VPC, it is usefull in production environment.

- Security Groups: controlling inbound and outbound traffic to EC2 instances.

- IAM authentication where access to AWS services like EC2 instance, AWS RDS etc is defined with least privileges, allowing to use only custom service accounts and accessing AWS services via SSO or AD within the organisation.

- Network ACLs: filtering traffic at the subnet level to add an extra layer of security.

- Application Load Balancing (ALB): distributing incoming traffic across multiple instances to improve availability, scalability and encrypting the data at rest and in transit.

- Monitoring: using Cloudwatch & CloudTrail to monitor & log Java application events as well as DB's events and also setup alerts in Pagerduty to manage critical incidents.

- Databases: AWS RDS is created within highly AZ's region as data retrieval for the Java application. There is also a read replica for fault tolerance as it continuously copies from primary DB so the data is replicated to point-in-time. 

Tools Used:

- Terraform
- CodePipeline/Jenkins
- CodeDeploy
- IAM
- Cloudwatch
- CloudTrail


When different AWS services are used to design 3-Tier application it is always a good practice that the infrastructure is immutable and easy to deploy. Such options include IaC (Infrastructure as a code) like Terraform, CI/CI pipeline like Cloudbuild Pipeline/Jenkins and CodeDeploy. 



