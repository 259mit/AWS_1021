## Section 1: Mannual Approval of CodeDeploy

This Case Study focussed on deploying an application or a webpage using Amazon Web Service (AWS) and store the website data in S3 Buckets, deploy the code but ensiure a manual approval of the commit from a third party account.

### Steps to solve the case study 1:

0. Assuming you have an AWS account and have successfully signed in, follow the below steps.
1. Set up an S3 bucket.
2. Then, set up an IAM Role, with EC2. Allot additional permissions of All Access S3.
3. Then set up another IAM Role: EC2 Role 
4. Set up an EC2 instance, by selecting launch instance.
5. Make sure you select the specified IAM role and create the tags. Add the code:

```
#!/bin/bash
sudo yum -y update
sudo yum -y install ruby
sudo yum -y install wget
cd /home/ec2-user
wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install
sudo chmod +x ./install
sudo ./install auto
sudo yum install -y python-pip
sudo pip install awscli
```

6. Then, move to the S3 bucket and upload the SampleApp_Linux.

<img src="https://github.com/259mit/AWS_1021/blob/8a2011b08f12164ff9a20164fd523a9414ea4d33/CodeDeploy/Snapshots/BucketDeploy.jpg" width=600>


<img src="https://github.com/259mit/AWS_1021/blob/8a2011b08f12164ff9a20164fd523a9414ea4d33/CodeDeploy/Snapshots/BucketApp.jpg" width=600>

7. Once this is done move to CodeDeploy and CodePipeline.
8. In CodePipeline, set up start new Application deployment and deployment group.
9. Select storage as S3, select the bucket and enable versioning. Follow other steps and deploy.
10. Once deployed in the pipeline, change the source file in S3, with the updated SampleApp_Linux.

#### Previous SampleApp_Linux

<img src="https://github.com/259mit/AWS_1021/blob/8a2011b08f12164ff9a20164fd523a9414ea4d33/CodeDeploy/Snapshots/SampleApp_Linux.jpg" width=600>

#### Updated SampleApp_Linux

<img src="https://github.com/259mit/AWS_1021/blob/8a2011b08f12164ff9a20164fd523a9414ea4d33/CodeDeploy/Snapshots/SampleApp_Linux_Updated.jpg" width=600>

11. Record the changes in Pipeline.
12. You are all set to proceed to the Manual Approval.
13. First create an IAM role of CodePipelineApproval, Move to creating a new IAM role and select 'Another AWS account' then specify account ID.
14. Then go to SNS and follow the dorections. Set up Email based notification.

<img src="https://github.com/259mit/AWS_1021/blob/bf5d3dfd9772f2d17bf9a9af202176752bad7769/CodeDeploy/Snapshots/SNS.jpg" width=600>

<img src="https://github.com/259mit/AWS_1021/blob/bf5d3dfd9772f2d17bf9a9af202176752bad7769/CodeDeploy/Snapshots/SNS%20email.jpg" width=600>

<img src="https://github.com/259mit/AWS_1021/blob/bf5d3dfd9772f2d17bf9a9af202176752bad7769/CodeDeploy/Snapshots/SNS%20Email%202.jpg" width=600>

<img src="https://github.com/259mit/AWS_1021/blob/bf5d3dfd9772f2d17bf9a9af202176752bad7769/CodeDeploy/Snapshots/SNS%20confirm.jpg" width=600>

15. You are all set with manual approval. 
16. The recipient should accept the invitation.
17. Then test the application commit.
    
a
