**Creating a VPC for your Amazon EKS cluster**

**Only Public Subnets:**

This VPC has three public subnets that are deployed into different Availability Zones in an AWS Region. All nodes are automatically assigned public IPv4 addresses and can send and receive internet traffic through an internet gateway. A security group is deployed that denies all inbound traffic and allows all outbound traffic. The subnets are tagged so that Kubernetes can deploy load balancers to them.

**To create your VPC**

1.  Open the AWS CloudFormation console at https://console.aws.amazon.com/cloudformation.
2.  From the navigation bar, select an AWS Region that supports Amazon EKS.
3.  Choose **Create stack**, With new resources (standard).
4.  Under Prepare template, make sure that **Template is ready** is selected and then under Template source, select **Amazon S3 URL**.
5.  Paste the following URL into the text area under **Amazon S3 URL** and choose **Next**:
    https://s3.us-west-2.amazonaws.com/amazon-eks/cloudformation/2020-10-29/amazon-eks-vpc-sample.yaml
6.  On the **Specify Details** page, enter the parameters, and then choose **Next**. 
    a)  **Stack name**: Choose a stack name for your AWS CloudFormation stack. For example, you can call it amazon-eks-vpc-sample. The name can contain only alphanumeric   characters (case-sensitive) and hyphens. It must start with an alphabetic character and can't be longer than 100 characters.

    b)  **VpcBlock:** Choose a CIDR block for your VPC. Each node, pod, and load balancer that you deploy is assigned an IPv4 address from this block. The default IPv4 values    provide enough IP addresses for most implementations, but if it doesn't, then you can change it. For more information, see VPC and subnet sizing in the Amazon VPC User Guide. You can also add additional CIDR blocks to the VPC once it's created.

    c)  **Subnet01Block**: Specify a CIDR block for subnet 1. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it.

    d) **Subnet02Block:** Specify a CIDR block for subnet 2. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it.

    e) **Subnet03Block:** Specify a CIDR block for subnet 3. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it.

7.  (Optional) On the **Options** page, tag your stack resources. Choose **Next**.

8.  On the **Review** page, choose **Create**.

9.  When your stack is created, select it in the console and choose **Outputs**.

10. Record the **VpcId** for the VPC that was created. You need this when you create your cluster and nodes.

11. Record the **SubnetIds** for the subnets that were created. You need at least two of these when you create your cluster and nodes.
