# To access remote repository from the AWS CLI:  
<br>

**1. To create Identity Provider	[Add OIDC Provider]**  
IAM  
Identity provider > Add provider    
Provider type: **OpenID Connect**  
Provider URL: **https://token.actions.githubusercontent.com**    
Audience: **sts.amazonaws.com** > Add provider  
<br>
<br>
**2. To Create IAM Role --> web identity**  
IAM Role > Create role    
Trusted entity type: **web identity**    
**Web identity-->**  
Identity provider: Select provider --> **token.actions.githubusercontent.com**  
Audience: **sts.amazonaws.com**    
GitHub organization name: **github-account-name** > Next  
GitHub Repository: **repository-name**  
GitHub branch: optional > Next  
Permissions policies: **AmazonS3FullAccess**	[AWS managed permission]  
Role name: **s3-read-access-rol** > Create role  

**3. Create and test workflow**  
Update/Configure web identity as below:  
role-to-assume: **Copy the ARN of IAM Role s3-read-access**  
aws-region: **region**  

Open github.com >  
Actions > Simple workflow > Configure   
Workflow Name: **aws-oidc-demo.yml** [filename]  

**Copy Use case:**  
name: AWS OIDC Challenge  
on: workflow_dispatch  
permissions:  
  id-token: write  
  contents: read  
jobs:  
  test-aws-oidc:  
    runs-on: ubuntu-latest  
    steps:  
      - uses: actions/checkout@v4  
      - uses: aws-actions/configure-aws-credentials@v4  
        with:  
          role-to-assume: **ARN-of-IAMRole-s3-read-access**  
          aws-region: **region**  
      - run: aws sts get-caller-identity  
      - run: aws s3 ls  

**> Commit change**  

**Test the workflow**  
github.com > Attach > workflow  
Select work flow: **aws-oidc-demo.yml**  
Run workflow > workflow  
From left panel, click on work flow  

