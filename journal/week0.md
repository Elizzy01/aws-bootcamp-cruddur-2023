# Week 0 — Billing and Architecture

## Prerequisities
 - Created AWS account for the bootcamp
 - Created Github repo
 - Set up Gitpod account 

## Required Homework
1. Attended the live stream
2. Watched the follow up videos for Week 0 - Generating credentials, Budget, Billing Alarms, AWS CLI videos

### Account security
3. Took certain security considerations on setting up the account
    - I set up an AWS organization and my bootcamp account as a sub-account. - *Even though I had created the account some months back. I retained the account because I have some credits on it which I would like to use for the bootcamp.*
    - I activated MFA on my account and root account using a virtual MFA app on my mobile phone called **Authy by Twilio**
  
  ![Security considerations for my user account](assets/Week%200-IAM%20security%20recommendations.png)
  
    - I gave my user admin role.
![Admin role to my IAM user](assets/Week0%20-AWS%20Admin%20-user.png)

### Architecture Diagrams

4. I created Architectural diagram, both the **Conceptual** and the **Logical** diagrams on Lucid Chart. I also did a little work with napkin.
Napkin
   ![Napkin Diagram](assets/Week0%20-%20Napkin%20image.jpg)
    - [Cruddur Conceptual Diagram](https://lucid.app/lucidchart/d0099a6b-c439-49d6-9cd0-6ae210eb165e/edit?invitationId=inv_542f629e-965d-4657-8013-154f306e223e)
   
   ![Conceptual Diagram](assets/_Cruddur%20-%20Conceptual%20Diagram%20(1).png)
   
    - [Cruddur Logical Diagram](https://lucid.app/lucidchart/a5a64e5f-b0f1-40a0-88d6-8ce213c7d2e0/edit?viewport_loc=63%2C-255%2C3469%2C1747%2C0_0&invitationId=inv_55f3b14f-5f06-4c63-84af-845bfaaf1f5d)
  ![Conceptual Diagram](assets/Cruddur%20Logical%20Architecture%20Diagram%20(1).png)
   
5.Used Cloudshell in us-east-1 region and it worked so well. :)
![Cloudshell showing AWS Credentials](assets/Week0%20-AWS%20Cloudshell.png)

6. I created Access key on my IAM console under the user security credentials. I then used Generated AWS Credentials - Access Key/Secret pair for cruddur-admin user. Added persistent Gitpod variables to store AWS credentials for resuse using these commands:

`gp env AWS_ACCESS_KEY_ID="" 
gp env AWS_SECRET_ACCESS_KEY=""
gp env AWS_DEFAULT_REGION=""`

## Homework Challenges
  - Created Architecture diagram on Napkins
  - 
