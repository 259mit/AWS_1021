# Cloud Computing Case Study 1 & 2 Documentation

#### By: Mithesh Ramachandran
#### Under the guidance of: Prof. Ankit Shah

------------------------------------------------

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

------------------------------------------------
    
## Section 2: Alexa Skills

This Case Study focussed on testing custom Alexa Skills with user defined output to specific commands using the Alexa Developer Console and AWS Lambda.

0. Assuming you have an AWS account and have successfully signed in, follow the below steps.
1. Set up an S3 bucket.

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/bucketlist.jpg" width=600>

2. Create MP3 files that you want to add in Amazon S3 bucket that you created.
3. So, head over to Amazon Polly, create audio files.

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/Lambda%204.jpg" width=600>

4. Click on save to S3 and enter the name of the bucket you just created.

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/Lambda%205.jpg" width=600>

5. Example audio mp3 file: [1.mp3](AlexaWithS3/Buckets/1.mp3)
6. Save 3 audio files.
7. Head over to S3 and rename the files as 1.mp3, 2.mp3 and 3.mp3

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/bucketobject.jpg" width=600>

8. The next part would be to create a lambda function.
9. So head over to AWS lambda and click on create function.
10. Follow the steps and come back to lambda home page. Now click on the function you just created.

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/Lambda%201.jpg" width=600>

11. Scroll down and head over to Code Source.

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/Lambda%202.jpg" width=600>

12. Now go to index.js and paste the contents of the file [index.js](AlexaWithS3/Lambda/alexa_lambda.txt).
13. Head over to lines 40-60 and change the 4 mp3 links with your S3 mp3 links. To do that head over to S3 bucket you made, select a file and copy object path/URL.

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/IndexNodeJsAddS3.jpg" width=600>

14. Now click on deploy

15. Copy the function ARN.

<img src="https://github.com/259mit/AWS_1021/blob/bdac297a373ffb73887f316aeec5ede21280b584/AlexaWithS3/Snapshots/Lambda%203.jpg" width=600>

16. Now head over to Alexa Developer Console.
17. Click on create skill. Select Fact (second option in the first prompt and continue with the second prompt)

<img src="https://github.com/259mit/AWS_1021/blob/c20f589cc5e0ca3c9237dd7141e682d14596a477/AlexaWithS3/Snapshots/step%201.jpg" width=600>

18. Head over to created skill and select involcation name

<img src="https://github.com/259mit/AWS_1021/blob/18445e740624642d8b851c01d11e68629e86df8a/AlexaWithS3/Snapshots/step%202.jpg" width=600>

19. Head over to endpoints. Now in the highlighted default endpoint paste the lambda function ARN that you copied.

<img src="https://github.com/259mit/AWS_1021/blob/18445e740624642d8b851c01d11e68629e86df8a/AlexaWithS3/Snapshots/step%203.jpg" width=600>

20. Next, head over to interfaces and tick the two sections.

<img src="https://github.com/259mit/AWS_1021/blob/18445e740624642d8b851c01d11e68629e86df8a/AlexaWithS3/Snapshots/step%204a.jpg" width=600>

<img src="https://github.com/259mit/AWS_1021/blob/18445e740624642d8b851c01d11e68629e86df8a/AlexaWithS3/Snapshots/step%204b.jpg" width=600>

21. Next, Head over to interaction model > Intents. Select the highlighted intent.

<img src="https://github.com/259mit/AWS_1021/blob/18445e740624642d8b851c01d11e68629e86df8a/AlexaWithS3/Snapshots/step%205.jpg" width=600>

22. Next, Enter a command to invoke the intent followed by {audio_input). Click on the plus sign at the right.
23. Make sure you have setting set similar to the images.

<img src="https://github.com/259mit/AWS_1021/blob/18445e740624642d8b851c01d11e68629e86df8a/AlexaWithS3/Snapshots/step%206.jpg" width=600>

24. Scroll down and click on audio_input and select slot type as AMAZON.NUMBER

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/step%207.jpg" width=600>

25. Enter a speech prompt

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/step%208.jpg" width=600>

26. Save and Build model.

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/step%209.jpg" width=600>

27. Next, click on test.
28. Enable microphone access and make sure test is in development, then select English US as language.

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/test%201.jpg" width=600>

29. Enter your skill invocation name. It will throw an error.

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/test%203.jpg" width=600>

30. Next enter your command to invoke intent.

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/test%204.jpg" width=600>

31. Alexa will display the prompt that you set.
32. Now enter a number
33. Alexa will start playing your audio. You can change the 'Playing Audio 1 text in the lamda index.js code that we entered, just before the URL.

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/test%205.jpg" width=600>

34. To enter more, follow your intent command and a number as a single command.

<img src="https://github.com/259mit/AWS_1021/blob/9c4a97bda67ce5c199f6a5ab880a03dd6d7d3e3e/AlexaWithS3/Snapshots/test%206.jpg" width=600>

35. Congratulations. You have completed the Case Study.


