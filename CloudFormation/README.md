#Creating an EC2 instance using CloudFormation Template  
###Description  
A simple CloudFormation template to create an EC2 instance  

###Resources Created:  
1. AWS EC2 Instance (Type: AWS::EC2::Instance)  

**Key Properties:** 

AMI ID: ami-060a84cbcb5c14844
Instance Type: t2.micro
Key Pair Name: aws_ec2_login
Tags:
    Name: sampleInstance

**How to Use:**  
1. In the AWS Console, go to CloudFormation Service.
2. Click on Create Stacl and upload the template.
3. Fill the required details.
4. On clicking Create, monitor the stack creation.
5. Once the stack creation is completed, go to EC2 instances and check whether the instance is created.


During the creation of the stack, got the following error,  
**Properties validation failed for resource MySampleEC2Instance with message: [#/Tags: expected type: JSONArray, found: JSONObject]**  
This error is related to the Tags section. Fixed this error by wrapping the tags inside a list.  

<ins>To test Drift Detection:</ins>
Terminate the created EC2 instance.  
Under CloudFormation -> Stacks -> ec2-sample-cft, check the Drift status by selecting the Stack and then choosing Drifts from the left pane.  
Click on the Detect stack drift.  
If there is any change in the stack created, it will show the status as DRIFTED. Since, the instance is terminated, the status should be displayed as DRIFTED.  
If any further details about the drift are required, select the resource under Resource drift status and click on View Drift details.  
