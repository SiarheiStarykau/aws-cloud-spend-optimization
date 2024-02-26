# Cloud Spend Optimization
This repository contains a list of tips and tricks for cloud spend optimization.

Cloud spend can be optimized in two ways:

- Remediate the things without solution modification
- Re-architect the solution for cost optimization

## AWS

### RDS
- [ ] **Snapshots and retention period.**
  - Are there old snapshots no longer needed?
  - Are the snapshots stored for a proper period of time?
- [ ] **Instance class.** Database services evolve, offering better cost/performance ratio. Take a look at the modern instance classes:
  - [Graviton](https://aws.amazon.com/blogs/aws/new-amazon-rds-on-graviton2-processors/)
  - [Aurora IOPS optimized](https://aws.amazon.com/about-aws/whats-new/2023/05/amazon-aurora-i-o-optimized/)
- [ ] **Unused/forgotten instances.** Stop them if they are not needed.

### Compute
- [ ] [**Reserved instances**](https://aws.amazon.com/ec2/pricing/reserved-instances/) and [**Savings Plans**](https://aws.amazon.com/savingsplans/). Planning ahead and using a flexible pricing model can reduce the cost significantly. 
- [ ] Consider using **higher generation EC2 instances.** They can offer better cost-performance ratios. Check [here](https://instances.vantage.sh/).
- [ ] Consider using [**Spot Instances**](https://aws.amazon.com/ec2/spot) for non-production workloads if possible.
- [ ] **Schedule instances** if possible. Use [AWS Instance Scheduler](https://aws.amazon.com/solutions/implementations/instance-scheduler-on-aws/).
- [ ] **Over-provisioned and low-utilized instances.** Check [Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/cost-optimization-checks.html#low-utilization-amazon-ec2-instances) and downgrade if possible.
- [ ] **Unattached EBS volumes.** Remove if they are not needed. Check [Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/cost-optimization-checks.html#underutilized-amazon-ebs-volumes) for help.
- [ ] Review and modify **EC2 Autoscaling Groups Configuration** to match actual demand, avoiding overprovisioning.

### S3
- [ ] **Old/forgotten objects.** Remove if no longer needed.
- [ ] **Use [S3 storage classes](https://aws.amazon.com/s3/storage-classes/)** to reduce costs on less frequently accessed data.
- [ ] **Lifecycle policies.** These [policies](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html) allow to automatically remove the objects after some time, or move them to a more cost-effective storage.
- [ ] **Reduce number of requests to Amazon S3 Glacier** when [storing huge amount of files](https://aws.amazon.com/blogs/storage/compressing-and-archiving-logs-to-the-amazon-s3-glacier-storage-classes/).

### Other
- [ ] Use Autoscaling or On-demand for [**Amazon DynamoDB**](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-cost-optimization.html).
- [ ] **Load Balancers**.
  - Remove idle/unused load balancers.
  - [Optimize](https://aws.amazon.com/blogs/networking-and-content-delivery/elb-maximizing-benefits-and-keeping-costs-low/) the usage.
  - Use [Application Load Balancers](https://medium.com/cognitoiq/how-cognitoiq-are-using-application-load-balancers-to-cut-elastic-load-balancing-cost-by-90-78d4e980624b) instead of classic load balancers.
  - Check how the [pricing](https://aws.amazon.com/elasticloadbalancing/pricing/) works.
- [ ] Optimize [**Elastic IP usage**](https://www.finout.io/blog/how-to-avoid-elastic-ip-cost-issues).
- [ ] Check [**CloudWatch Log Group retention policies**](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html).
- [ ] Check unused [**Kinesis Data Streams**](https://aws.amazon.com/kinesis/data-streams/pricing/).

### Tools
- [ ] [AWS Pricing Calculator](https://calculator.aws/#/)
- [ ] [Cost Explorer](https://aws.amazon.com/blogs/aws-cloud-financial-management/getting-started-with-aws-cost-explorer-part-1/)
- [ ] [Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/) 
- [ ] [EC2 Utilization Tool](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_ec2.html)
- [ ] [AWS Billing](https://aws.amazon.com/aws-cost-management/aws-billing/)
- [ ] [S3 Storage Lens](https://aws.amazon.com/blogs/aws/s3-storage-lens/)
- [ ] [AWS Budgets](https://aws.amazon.com/aws-cost-management/aws-budgets/)
- [ ] [AWS Cost Categories](https://aws.amazon.com/aws-cost-management/aws-cost-categories/)
- [ ] [AWS Cost Anomaly Detection](https://aws.amazon.com/aws-cost-management/aws-cost-anomaly-detection/)
- [ ] [AWS Purchase Order Management](https://aws.amazon.com/aws-cost-management/aws-purchase-order-management/)
- [ ] [Reserved Instance Reporting](https://aws.amazon.com/aws-cost-management/reserved-instance-reporting/)
- [ ] [AWS Application Cost Profiler](https://aws.amazon.com/aws-cost-management/aws-application-cost-profiler/)
- [ ] [AWS Cost and Usage Reports](https://aws.amazon.com/aws-cost-management/aws-cost-and-usage-reporting/)
- [ ] [AWS Compute Optimizer](https://aws.amazon.com/compute-optimizer/)
- [ ] Consider using third-party tools for cost optimization.
- [ ] Set up cloud usage culture and best practices in your organization. Set up a periodical cloud spend review process. 

### Re-architecting
- [ ] Number of I/O requests to RDS and S3.
  - Can the application be updated to reduce the number of requests?
  - Can the batch processing be used?
- [ ] Consider going [serverless](https://aws.amazon.com/serverless/).

### Reading
- [ ] [Cost Optimization Pillar - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html)
- [ ] [Cloud Financial Management with AWS](https://aws.amazon.com/aws-cost-management/)
- [ ] [10 things you can do today to reduce AWS costs](https://aws.amazon.com/blogs/compute/10-things-you-can-do-today-to-reduce-aws-costs/)
- [ ] [AWS Credits](https://aws.amazon.com/free/offers/)
- [ ] [How to reduce your AWS costs? Save up to $500k with these guidelines!](https://george-51059.medium.com/reduce-aws-costs-74ef79f4f348)
