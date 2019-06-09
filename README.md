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
    
    
