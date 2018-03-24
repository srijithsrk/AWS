


<h3>Determine appropriate use of multi-Availability Zones vs. multi-Region architectures</h3>

1. Multi-AZ services examples are S3, RDS, DynamoDB. Using multi-AZ can mitigate against the loss of up to two AZs (data centres, assuming there are three. Some regions only have two). This can provide a good balance between cost, complexity and reliability
2. Multi-region services can mitigate failures in AZs or individual regions, but may cost more and introduce more infrastructure and complexity. Use ELB for multi-region failover and resilience, CloudFront
3. DynamoDB offers cross region replication, RDS offers the ability to snapshot from one region to another to have read only replicas. Code Pipeline has a built in template for replicating DynamoDB elsewhere for DR
4. Redshift can snapshot within the same region and also replicate to another region

<h3>Demonstrate ability to implement self-healing capabilities</h3>

1. HA available already for most popular databases:-
2. SQL Server Availability Groups, SQL Mirroring, log shipping. Read replicas in other AZs not supported
3. MySQL – Asynchronous mirroring
4. Oracle – Data Guard, RAC (RAC not supported on AWS but can run on EC2 by using VPN and Placement Groups as multicast is not supported)
5. RDS has multi-AZ automatic failover to protect against
6. Loss of availability in primary AZ
7. Loss of connectivity to primary DB
8. Storage or host failure of primary DB
9. Software patching (done by AWS, remember)
10. Rebooting of primary DB
11. Uses master and slave model
12. MySQL, Oracle and Postgres use physical layer replication to keep data consistent on the standby instance
13. SQL Server uses application layer mirroring but achieves the same result
14. Multi-AZ uses synchronous replication (consistent read/write), asynchronous (potential data loss) is only used for read replicas
15. DB backups are taken from the secondary to reduce I/O load on the primary
16. DB restores are taken from the secondary to avoid I/O suspension on the primary
17. AZ failover can be forced by rebooting your instance either via the console or via the RebootDBInstance API call
18. Multi-AZ databases are used for DR, not as a scaling solution. Scale can be achieved by using read replicas, this can be done via the AWS console or by using the CreateDBInstanceReadReplica API call
19. Amazon Aurora employs a highly durable, SSD-backed virtualized storage layer purpose-built for database workloads. 
20. Amazon Aurora automatically replicates your volume six ways, across three Availability Zones. Amazon Aurora storage is fault-tolerant, transparently handling the loss of up to two copies of data without affecting database write availability and up to three copies without affecting read availability. Amazon Aurora storage is also self-healing. Data blocks and disks are continuously scanned for errors and replaced automatically.
21. Creating a read replica means a snapshot of your primary DB instance, this may result in a pause of about a minute in non multi-AZ deployments
22. Multi-AZ deployments will use a secondary for a snapshot
23. A new DNS endpoint address is given for the read only replica, you need to update the app
24. You can promote a read only replica to be a standalone, but this breaks replication
25. MySQL and Postgres can have up to 5 replicas
26. Read replicas in different regions for MySQL only
26. Replication is asynchronous only
27. Read replicas can be built off Multi-AZ databases
28. Read replicas are not multi-AZ
29. MySQL can have read replicas of read replicas, but this increases latency
30. DB Snapshots and automated backups cannot be taken of read replicas
31. Consider using DynamoDB instead of RDS if your database does not require:-
32. Transaction support
33. Atomicity
34. Consistency
35. Isolation
36. Durability
37. ACID (durability) compliance
38. Joins
39. SQL

<i><a href="https://blue-clouds.com/2016/06/21/21-06-16/">Credits to Chris Beckett @ BlueClouds</a>

<h2>Passing the AWS solutions architect - Professional exam > General Learning Material</h2>
To prepare at best for the exam you should start with an overview of the concepts and knowledge areas covered on the exam and walks you through the exam structure and question formats. Get an hands-on practice with advanced use cases, while practice exam questions test your understanding of key architectural concepts. 

1. <a href="https://cloudacademy.com/learning-paths/solutions-architect-professional-aws-17/">Solutions Architect—  Professional Certification for AWS (2016)</a>
2. <a href="https://cloudacademy.com/ebooks/guide-aws-certification-exams-2/">A Guide to AWS Certification Exams</a>
3. <a href="https://www.dropbox.com/s/hizoeicmgf4iha5/DDoS_White_Paper_June2015.pdf">AWS Best Practices for DDoS Resiliency</a>
4. <a href="https://aws.amazon.com/kinesis/streams/faqs/">Amazon Kinesis Streams FAQs</a>
5. <a href="https://docs.aws.amazon.com/streams/latest/dev/kinesis-dg.pdf">Amazon Kinesis Streams: Developer Guide</a>
6. <a href="http://docs.aws.amazon.com/IAM/latest/UserGuide/iam-ug.pdf">AWS Identity and Access Management User Guide</a>
6. <a href="https://aws.amazon.com/it/cloudfront/dynamic-content/">Amazon CloudFront - Dynamic Content Delivery</a>
7. <a href="https://aws.amazon.com/it/redshift/faqs/">Amazon Redshift FAQs</a>
8. <a href="http://cloudacademy.com/blog/amazon-aws-certified-solutions-architect-what-to-study-tips-and-resources/">Amazon AWS Certified Solutions Architect: What to Study, Tips and Resources</a>
9. <a href="http://nineofclouds.blogspot.ch/2013/01/vpc-migration-nats-bandwidth-bottleneck.html">VPC Migration: NATs & Bandwidth Bottleneck</a>
10. <a href="https://docs.aws.amazon.com/sns/latest/dg/sns-dg.pdf">Amazon Simple Notification Service Developer Guide</a>
11. <a href="http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-dg.pdf">Amazon Simple Storage Service Developer Guide</a>
12. <a href="https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-ug.pdf">Amazon Virtual Private Cloud User Guide
</a>
13. <a href="http://d0.awsstatic.com/whitepapers/migration-best-practices-rdbms-to-dynamodb.pdf">Best Practices for Migrating from RDBMS to Amazon DynamoDB</a>
14. <a href="http://cloudacademy.com/blog/aws-certification-exams-what-to-expect/">AWS Certification Exams: What to expect at the Exam
</a>
15. <a href="http://blogs.aws.amazon.com/security/post/Tx71TWXXJ3UI14/Enabling-Federation-to-AWS-using-Windows-Active-Directory-ADFS-and-SAML-2-0">Enabling Federation to AWS Using Windows Active Directory, ADFS, and SAML 2.0</a>
16. <a href="https://d0.awsstatic.com/Train%20&%20Cert/docs/AWS_certified_solutions_architect_professional_examsample.pdf">AWS Certified Solutions Architect – Professional Level Sample Exam Questions</a>
17. <a href="https://d0.awsstatic.com/training-and-certification/docs-sa-pro/AWS_certified_solutions_architect_professional_blueprint.pdf">AWS Certified Solutions Architect Professional Exam Blueprint
</a>
18. <a href="https://www.youtube.com/watch?v=iJeiWU9Ud7w">Cloud Architectures with AWS Direct Connect (ARC304) | AWS re:Invent 2013</a>
19. <a href="https://www.youtube.com/watch?v=Ut5TG1ueU1E">AWS re: Invent STG 204: Using AWS Storage Gateway</a>
20. <a href="https://www.youtube.com/watch?v=k32FaqM40rw">Storage TCO using AWS Storage Gateway, Amazon S3 and Amazon Glacier (STG202) | AWS re:Invent 2013</a>
21. <a href="https://www.youtube.com/watch?v=wioDkHQ9Pm8&index=10&list=PLhr1KZpdzuketO0VQtLwchbqJLO4vDjAq">AWS re:Invent 2014 | (ARC206) Architecting Reactive Applications on AWS (Playlist)</a>
22. <a href="https://www.youtube.com/watch?v=n6eL9W1Go08">AWS June Webinar Series - Deep dive: Hybrid Architectures</a>
23. <a href="https://d0.awsstatic.com/training-and-certification/docs-sa-pro/AWS_certified_solutions_architect_professional_blueprint.pdf">AWS January 2016 Webinar Series - Managing your Infrastructure as Code</a>
24. <a href="https://iam.cloudonaut.io/">Complete AWS IAM Reference</a>
25. <a href="https://cloudonaut.io/templates-for-aws-cloudformation/">Free Templates for AWS CloudFormation</a>
26. <a href="https://cloudacademy.com/webinars/how-study-aws-solutions-architect-professional-certification-24/">How to study for the AWS Solutions Architect Professional Certification (Webinar)</a>
27. <a href="https://soundcloud.com/cloudacademyinc/cloud-academy-office-hours-aws-certifications-special-guest">Interview with 5 AWS Certified Greg Cockburn (Podcast)</a>
28. <a href="https://soundcloud.com/cloudacademyinc/cloud-academy-office-hours-special-guest">Interview with 5 AWS Certified Stephen Wilding (Podcast)</a>
<br>
<h2>Passing the AWS solutions architect - Professional Exam > Blueprints Exam</h2>

<p>In <a href="https://d0.awsstatic.com/Train%20&%20Cert/docs/AWS_certified_solutions_architect_professional_examsample.pdf">this PDF</a> you can download the Sample Question provided by AWS We reviewed all the questions provided by AWS and you can find the correct answers marked in bold.</p>

> Which AWS based disaster recovery strategy will give you the best RTO?

<b>A) Deploy the Oracle database and the JBoss app server on EC2. Restore the RMAN Oracle backups from
Amazon S3. Generate an EBS volume of static content from the Storage Gateway and attach it to the
JBoss EC2 server.<br></b>
B) Deploy the Oracle database on RDS. Deploy the JBoss app server on EC2. Restore the RMAN Oracle
backups from Amazon Glacier. Generate an EBS volume of static content from the Storage Gateway and
attach it to the JBoss EC2 server.<br>
C) Deploy the Oracle database and the JBoss app server on EC2. Restore the RMAN Oracle backups from
Amazon S3. Restore the static content by attaching an AWS Storage Gateway running on Amazon EC2
as an iSCSI volume to the JBoss EC2 server.<br>
D) Deploy the Oracle database and the JBoss app server on EC2. Restore the RMAN Oracle backups from
Amazon S3. Restore the static content from an AWS Storage Gateway-VTL running on Amazon EC2<br>

> An ERP application is deployed in multiple Availability Zones in a single region. In the event of failure, the
RTO must be less than 3 hours, and the RPO is 15 minutes. The customer realizes that data corruption
occurred roughly 1.5 hours ago. Which DR strategy can be used to achieve this RTO and RPO in the
event of this kind of failure?

A) Take 15-minute DB backups stored in Amazon Glacier, with transaction logs stored in Amazon S3 every
5 minutes.<br>
B) Use synchronous database master-slave replication between two Availability Zones.<br>
<b>C) Take hourly DB backups to Amazon S3, with transaction logs stored in S3 every 5 minutes.<br></b>
D) Take hourly DB backups to an Amazon EC2 instance store volume, with transaction logs stored in
Amazon S3 every 5 minutes.<br>

> The Marketing Director in your company asked you to create a mobile app that lets users post sightings
of good deeds known as random acts of kindness in 80-character summaries. You decided to write the
application in JavaScript so that it would run on the broadest range of phones, browsers, and tablets.
Your application should provide access to Amazon DynamoDB to store the good deed summaries. Initial
testing of a prototype shows that there aren’t large spikes in usage. Which option provides the most costeffective
and scalable architecture for this application?

A) Provide the JavaScript client with temporary credentials from the Security Token Service using a Token
Vending Machine (TVM) on an EC2 instance to provide signed credentials mapped to an Amazon Identity
and Access Management (IAM) user allowing DynamoDB puts and S3 gets. You serve your mobile
application out of an S3 bucket enabled as a web site. Your client updates DynamoDB.<br>
<b>B) Register the application with a Web Identity Provider like Amazon, Google, or Facebook, create an IAM
role for that provider, and set up permissions for the IAM role to allow S3 gets and DynamoDB puts. You
serve your mobile application out of an S3 bucket enabled as a web site. Your client updates DynamoDB.<br></b>
C) Provide the JavaScript client with temporary credentials from the Security Token Service using a Token
Vending Machine (TVM) to provide signed credentials mapped to an IAM user allowing DynamoDB puts.
You serve your mobile application out of Apache EC2 instances that are load-balanced and autoscaled.
Your EC2 instances are configured with an IAM role that allows DynamoDB puts. Your server updates
DynamoDB.<br>
D) Register the JavaScript application with a Web Identity Provider like Amazon, Google, or Facebook,
create an IAM role for that provider, and set up permissions for the IAM role to allow DynamoDB puts.
You serve your mobile application out of Apache EC2 instances that are load-balanced and autoscaled.
Your EC2 instances are configured with an IAM role that allows DynamoDB puts. Your server updates
DynamoDB.<br>

> You are building a website that will retrieve and display highly sensitive information to users. The amount
of traffic the site will receive is known and not expected to fluctuate. The site will leverage SSL to protect
the communication between the clients and the web servers. Due to the nature of the site you are very
concerned about the security of your SSL private key and want to ensure that the key cannot be
accidentally or intentionally moved outside your environment. Additionally, while the data the site will
display is stored on an encrypted EBS volume, you are also concerned that the web servers’ logs might
contain some sensitive information; therefore, the logs must be stored so that they can only be decrypted
by employees of your company. Which of these architectures meets all of the requirements?

A) Use Elastic Load Balancing to distribute traffic to a set of web servers. To protect the SSL private key,
upload the key to the load balancer and configure the load balancer to offload the SSL traffic. Write your
web server logs to an ephemeral volume that has been encrypted using a randomly generated AES key.<br>
B) Use Elastic Load Balancing to distribute traffic to a set of web servers. Use TCP load balancing on the
load balancer and configure your web servers to retrieve the private key from a private Amazon S3
bucket on boot. Write your web server logs to a private Amazon S3 bucket using Amazon S3 server-side
encryption.<br>
C) Use Elastic Load Balancing to distribute traffic to a set of web servers, configure the load balancer to
perform TCP load balancing, use an AWS CloudHSM to perform the SSL transactions, and write your
web server logs to a private Amazon S3 bucket using Amazon S3 server-side encryption.<br>
<b>D) Use Elastic Load Balancing to distribute traffic to a set of web servers. Configure the load balancer to
perform TCP load balancing, use an AWS CloudHSM to perform the SSL transactions, and write your
web server logs to an ephemeral volume that has been encrypted using a randomly generated AES key.<br></b>

> You are designing network connectivity for your fat client application. The application is designed for
business travelers who must be able to connect to it from their hotel rooms, cafes, public Wi-Fi hotspots,
and elsewhere on the Internet. You do not want to publish the application on the Internet.
Which network design meets the above requirements while minimizing deployment and operational
costs?

A) Implement AWS Direct Connect, and create a private interface to your VPC. Create a public subnet and
place your application servers in it.<br>
B) Implement Elastic Load Balancing with an SSL listener that terminates the back-end connection to the
application.<br>
C) Configure an IPsec VPN connection, and provide the users with the configuration details. Create a public
subnet in your VPC, and place your application servers in it.<br>
<b>D) Configure an SSL VPN solution in a public subnet of your VPC, then install and configure SSL VPN client
software on all user computers. Create a private subnet in your VPC and place your application servers in
it.</br></b>

> Your company hosts an on-premises legacy engineering application with 900GB of data shared via a
central file server. The engineering data consists of thousands of individual files ranging in size from
megabytes to multiple gigabytes. Engineers typically modify 5-10 percent of the files a day. Your CTO
would like to migrate this application to AWS, but only if the application can be migrated over the
weekend to minimize user downtime. You calculate that it will take a minimum of 48 hours to transfer
900GB of data using your company’s existing 45-Mbps Internet connection.
After replicating the application’s environment in AWS, which option will allow you to move the
application’s data to AWS without losing any data and within the given timeframe?

A) Copy the data to Amazon S3 using multiple threads and multi-part upload for large files over the
weekend, and work in parallel with your developers to reconfigure the replicated application environment
to leverage Amazon S3 to serve the engineering files.<br>
<b>B) Sync the application data to Amazon S3 starting a week before the migration, on Friday morning perform
a final sync, and copy the entire data set to your AWS file server after the sync completes.</b><br>
C) Copy the application data to a 1-TB USB drive on Friday and immediately send overnight, with Saturday
delivery, the USB drive to AWS Import/Export to be imported as an EBS volume, mount the resulting EBS
volume to your AWS file server on Sunday.<br>
D) Leverage the AWS Storage Gateway to create a Gateway-Stored volume. On Friday copy the application
data to the Storage Gateway volume. After the data has been copied, perform a snapshot of the volume
and restore the volume as an EBS volume to be attached to your AWS file server on Sunday.<br>

<br>

<h2>The Exam Day</h2>

<b>Just a couple of suggestions to pass the AWS Solutions Architect Professional level certification:</b>

1. Wake up early every day and have a nice breakfast in the morning
2. No coffee, try to eat a banana and a cup of orange juice every morning 
3. Practice with [our specific resources for the AWS Certifications](https://cloudacademy.com/aws-certifications-training/)
4. Drink water every day
5. Get the most out of [this GitHub repository](https://gist.github.com/leonardofed/bbf6459ad154ad5215d354f3825435dc)
6. Rewatch the [AWS Solution Architect Professional level certification detailed study-guide with tips and tricks on how to pass the certification](https://cloudacademy.com/webinars/how-study-aws-solutions-architect-professional-certification-24/)
8. AWS Youtube channel: watch as many of the technical seminars and re:Invent presentations as you can. Then re-watch. Make notes.
9. I would say that your chance of passing the course if you have not have had any practical experience to be seriously compromised. You have no excuse, get an account, login and play.
10. Do some sport every day to reset your mind out of work and try to sleep 7h every night 
11. Repeat
12. Once you are feeling confident enough you are ready to take a practice exam [here](https://www.webassessor.com/wa.do?page=publicHome&branding=AMAZON)
13. Smile at least once every day 
14. Have fun

If you've found this gist useful you can follow me <a href="https://twitter.com/leonardofed">@leonardofed</a> for more info about AWS Certifications.
