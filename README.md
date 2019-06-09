# Automating-AWS-with-Lambda-Python-and-Boto3
Automating AWS with Lambda, Python, and Boto3

----------------------

- https://github.com/vaquarkhan/content-lambda-boto3

--------------------------


 
### Boto3

Run python3 interactively:

     python3

Run the following commands:

     >>> import boto3
     >>> sts = boto3.client('sts')
     >>> sts.get_caller_identity()

The output should look like this:

     {'UserId': 'AIDAJKLMNOPQRSTUVWXYZ', 'Account': '123456789012', 'Arn': 'arn:aws:iam::123456789012:user/devuser', 'ResponseMetadata':        {'RequestId': '3e310806-50c9-11e9-93ae-dbac86675630', 'HTTPStatusCode': 200, 'HTTPHeaders': {'x-amzn-requestid': '3e310806-50c9-11e9-      93ae-dbac86675630', 'content-type': 'text/xml', 'content-length': '404', 'date': 'Wed, 27 Mar 2019 19:48:06 GMT'}, 'RetryAttempts': 0}}

 
 
 
 
 Resources

    - Boto3 Documentation: https://boto3.amazonaws.com/v1/documentation/api/latest/index.html
    - Botocore Documentation: https://botocore.amazonaws.com/v1/documentation/api/latest/index.html
    - AWS Community Python Forum: https://forums.aws.amazon.com/forum.jspa?forumID=132
    
    
----------------------------------------

Creating an EC2 Instance with Lambda

In this lab, we will write a Lambda function that will create an EC2 instance. This Lambda function will be written in Python using the Boto3 library. We will also create a custom Lambda execution policy. When we're done, you will be able to SSH into the new EC2 instance.

Log in to the AWS environment using the credentials provided on the lab page.
Create EC2 Key Pair

    Navigate to EC2.
    In the navigation pane, under NETWORK & SECURITY, choose Key Pairs.
    Choose Create Key Pair.
    Enter a name for the new key pair (e.g., "ec2") in the Key pair name field of the Create Key Pair dialog box, and then choose Create.
    Save the private key file in a safe place. Note: Make sure you remember the name of your private key file and save it somewhere easily accessible.

Create Lambda Function

    Navigate to AWS Lambda.
    Click Create a function.
    Choose Author from scratch and use the following settings:
        Name: CreateEC2Instance
        Runtime: Python 3.7
        Role: Create a custom role
            Role name: Leave as-is
            Click View policy document.
                Click Edit.
                Paste in the policy from this file on GitHub.
                Click Allow.
    Click Create function.
    On the CreateEC2Instance function page, scroll down to the Function code section.
    Paste in the Python source code from this file on GitHub.
    Scroll down to the Environment variables section.
    Set the following environment variables:
        AMI
            Key: AMI
            Value: Open EC2 in a new browser tab, click Launch Instance, and copy and paste the ami value listed after Amazon Linux 2.
        INSTANCE_TYPE
            Key: INSTANCE_TYPE
            Value: t2.micro
        KEY_NAME
            Key: KEY_NAME
            Value: The name of the EC2 key pair you created earlier.
        SUBNET_ID
            Key: SUBNET_ID
            Value: Navigate to VPC > Subnets, and copy and paste the ID of one of the public subnets in your VPC.
    Save the Lambda function.

Test Lambda Function

    Click Test.
    Define an empty test event. Its contents can simply be {}.
    Give it any name you like.
    Click Create.
    Click Test.
    Observe that an EC2 instance is initializing.

Connect to the Instance via SSH

    Open a terminal session, and use the following command to set the permissions of your private key file so that only you can read it.

    chmod 400 <KEY-PAIR>.pem

    Replace <KEY-PAIR> with your key pair name.

    Connect via the public IP of the EC2 instance.

     ssh -i <KEY-PAIR>.pem ec2-user@<IP ADDRESS>

    Remember to replace <IP ADDRESS> with the public IP of the EC2 instance you created.

