## Identity and Access Management - IAM User, Group, and Policy

#### Better approach: Attach policies to groups and then add users to groups
<br>

**Practice in this order:**
1.	Create group.  
2.	Attach read-only policy to group.  
3.	Create user.  
4.	Add user to group.  
5.	Test allowed access.  
6.	Test denied access.  

**Lab 1 - S3 Read-Only Access**
<br>

**Create:**  
Group: S3ReadOnlyGroup  
Policy: AmazonS3ReadOnlyAccess  
User: learner-s3    

**Test:**  
Sign in as learner-s3.  
Confirm the user can view S3.  
Try creating or deleting something. It should fail.  
Capture the Access Denied result.  
<br>

**Step 01 - Create group: S3ReadOnlyGroup**     
IAM  
IAM user groups > Create group  
User group name: s3-readonlygroup  
<br>

**Step 02 - Create policy: AmazonS3ReadOnlyAccess and attach to the group**  
IAM  
Policies > Create policy
Policy editor: Visual/JSON  
Select a service: **s3**  
Access level: Select all List and Read  
Resources: All > Next
Policy name: s3-readonly > Create policy  

**Now, attach policy to the group**   

IAM user groups > exapnd group **s3-readonlygroup**  
Permissions > Add permissions > Attach policies  
Filter by type: Customer managed  
Select policy: **s3-readonly** > Attach policies  
<br>

<img width="724" height="422" alt="image" src="https://github.com/user-attachments/assets/8a087ea3-d3a1-4984-8c0f-d15ae92e4645" /><br>
<br>

**Step 03 - Create user: learner-s3 and attach to the group**  
IAM  
IAM users > Create user  
User name: learner-s3  
Select: Provide user access to the AWS management console - optional  
Console password: Custom password > Next  
Permissions options: Add user to group  
Select: group - **s3-readonlygroup** > Next > Review details > Create user  
**Download .csv file** <-- console and useraccount details  
<br>

<img width="726" height="339" alt="image" src="https://github.com/user-attachments/assets/b2f3d3e6-ceca-47eb-9c37-6010a3151ea0" /><br>
<br>

**Step 04 - Test allowed/denied acess in different browser / Incognito mode**  
<br>

<img width="842" height="398" alt="image" src="https://github.com/user-attachments/assets/51847bb1-a010-49f1-9e65-fc2a5913cf75" /><br>
<br>
<br>
**List the s3 bucket**  
<br>
<img width="935" height="324" alt="image" src="https://github.com/user-attachments/assets/1d6fe808-a68c-4386-ae59-8f980a6a26ee" /><br>
<br>
<br>
**Able to list the s3 bucket**  

**Now, try creating folder in s3**  
<br>
<img width="935" height="206" alt="image" src="https://github.com/user-attachments/assets/e01dbea5-5bc0-42dc-891c-d7a368ef06bd" /><br>
<br>
**Failed to folder bucket in in s3**  
<br>
<br>

-----

## For Practice  

## Lab 2 - EC2 Read-Only Access  
Create:  
•	Group: EC2ReadOnlyGroup  
•	Policy: AmazonEC2ReadOnlyAccess  
•	User: learner-ec2  

Test:  
•	Sign in as learner-ec2.  
•	Confirm the user can open the EC2 dashboard.  
•	Confirm the user cannot create or terminate instances.  
<br>

## Lab 3 - Billing Read-Only Access  
Create:  
•	Group: BillingViewGroup  
•	Policy: AWSBillingReadOnlyAccess  
•	User: learner-billing  
Test:  
•	Sign in as learner-billing.  
•	Confirm the user can view the Billing Dashboard.  
•	Confirm the user cannot manage unrelated AWS services.  

