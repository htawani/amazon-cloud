# To configure AWS CLI on local machine  

### 1. Generate and download the access key ID and token  
IAM User > select-user >  
Security Credentials > Create Access key >  
Use case: CLI > Sign Agreement > Next >   
Description: AWS CLI access > Create access key  
Download .csv file > Done   
<br>
So, now we have the access key and token, we can configure AWS CLI  

### 2. Configure AWS CLI on local machine
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions<br>
<br>
**Select platform:** Linux, Windows, MAC to install  
Download AWS CLI v2  
Install AWS CLI v2  

$ **aws configure**  
Provide --> Key and secrete key  

$ **aws configure**

Tip: You can deliver temporary credentials to the AWS CLI using your AWS Console session by running the command 'aws login'.  
AWS Access Key ID [None]:  

**To access s3 bucket from AWS CLI**  
$ **aws s3 ls**  
