This VPC has three public subnets that are deployed into different Availability Zones in an AWS Region. All nodes are automatically assigned public IPv4 addresses and can send and receive internet traffic through an internet gateway. A security group is deployed that denies all inbound traffic and allows all outbound traffic. The subnets are tagged so that Kubernetes can deploy load balancers to them.

To create your VPC

Open the AWS CloudFormation console at https://console.aws.amazon.com/cloudformation.
From the navigation bar, select an AWS Region that supports Amazon EKS.
Choose Create stack, With new resources (standard).
Under Prepare template, make sure that Template is ready is selected and then under Template source, select Amazon S3 URL.
Paste the following URL into the text area under Amazon S3 URL and choose Next:
