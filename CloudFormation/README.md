# Creating an EC2 instance using CloudFormation Template  
### Description  
A simple CloudFormation template to create an EC2 instance  

### Resources Created:  
1. AWS EC2 Instance (Type: AWS::EC2::Instance)  

**Key Properties:** 

ImageId: ami-060a84cbcb5c14844  
InstanceType: t2.micro  
KeyName: aws_ec2_login  
Tags:  
    - Key: "Instance_Name"  
      Value: "sampleInstance"  

**How to Use:**  
1. In the AWS Console, go to CloudFormation Service.
2. Click on Create Stack and upload the template.
3. Fill the required details.
4. On clicking Create, monitor the stack creation.
![image](https://github.com/user-attachments/assets/e82ffdd9-0c25-4327-adb9-ac4281a84a0d)

5. Once the stack creation is completed, go to EC2 instances and check whether the instance is created.
![image](https://github.com/user-attachments/assets/29f49ec4-4087-49f4-b026-2b307ece6ba7)

During the creation of the stack, got the following error,  

**Properties validation failed for resource MySampleEC2Instance with message: [#/Tags: expected type: JSONArray, found: JSONObject]**  

This error is related to the Tags section. Fixed this error by wrapping the tags inside a list.  

<ins>To test Drift Detection:</ins>
Terminate the created EC2 instance. 
![image](https://github.com/user-attachments/assets/ac9b34a0-76fe-4a54-9aee-fea945bc0ac1)

Under CloudFormation -> Stacks -> ec2-sample-cft, check the Drift status by selecting the Stack and then choosing Drifts from the left pane.  
Click on the Detect stack drift.  
If there is any change in the stack created, it will show the status as DRIFTED. Since, the instance is terminated, the status should be displayed as DRIFTED.  
![image](https://github.com/user-attachments/assets/8410281a-744d-4da0-9116-b2c615bf6e9d)

If any further details about the drift are required, select the resource under Resource drift status and click on View Drift details.  
![image](https://github.com/user-attachments/assets/fc728d80-73ba-4333-96a9-a8873262e4ec)
