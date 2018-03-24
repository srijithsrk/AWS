

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
