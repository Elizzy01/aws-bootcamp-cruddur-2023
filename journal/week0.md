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
```
gp env AWS_ACCESS_KEY_ID=""
gp env AWS_SECRET_ACCESS_KEY=""
gp env AWS_DEFAULT_REGION=""
```

7. Installed AWS CLI for Gitpod using [this video.](https://www.youtube.com/watch?v=OdUnNuKylHg) Manually installed, but also edited .gitpod.yml to auto-install if the environment gets restarted.
```
tasks:
  - name: aws-cli
    env:
      AWS_CLI_AUTO_PROMPT: on-partial
    init: |
      cd /workspace
      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
      unzip awscliv2.zip
      sudo ./aws/install
      cd $THEIA_WORKSPACE_ROOT
```

8. Environment Variables in Gitpod
Confirmed in Gitpod [User Settings > Variables](https://gitpod.io/user/variables) that variables are saved:

![Gitpod variables](assets/Week%200-%20Gitpod%20Variables.png)

Started up a new Gitpod environment to confirm AWS CLI was installed correctly and AWS credentials were pulled from Gitpod variables to environment variables.  Successfully ran ```aws sts get-caller-identity``` and returned values.

9.  Created a Budget

  * Used the JSON from [this article](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/budgets/create-budget.html) to create a billing budget.  
  * I created two budgets, one for my credits and the other for my zero-bootcamp spend. 
  ![Budget set-up](assets/Week%200-Budgets.png)
  
   I configured the JSON files in the aws/json directory and ran the following command to create the budget:

  ```
  aws budgets create-budget \
    --account-id $AWS_ACCOUNT_ID \
    --budget file://aws-budget.json \
    --notifications-with-subscribers file://aws-budget-notifications-with-subscribers.json
  ```

  * Note that I have the AWS Account ID set as an environment variable in Gitpod so it can automatically be retrieved on workspace launch, rather than hardcoding.  I set this up in Gitpod via CLI using:
  
  ```
  gp env AWS_ACCOUNT_ID=""
  ```

  * I also created an SNS topic as a billing alarm, to email me if the usage is at 50%, 80% and $100.  I ran the following to create a Topic ARN, and once it was generated, ran the next command to subscribe SNS to the billing alarm and to notify me when in alarm:

  ```
  aws sns create-topic --name billing-alarm

  aws sns subscribe \
    --topic-arn="<billing-alarm-arn>" \
    --protocol=email \
    --notification-endpoint=emailaddress@gmail.com
```

* I checked my email address, and confirmed the subscription so AWS will email me if the billing alarm goes off:

  
10.  Created a Billing Alarm (after Budget)

* [Used this document](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html) to set up a billing alarm using CloudWatch.
* Configured JSON file [here](../aws/json/aws-metric-alarm-config.json) with settings to breach alarm at $10 usage on one data point, and ran the following command in AWS CLI to set it up:

```
aws cloudwatch put-metric-alarm --cli-input-json file://aws-metric-alarm-config.json
```

I received an insufficient data state on one of my alarms, so I will wait to see if it addresses itself once data starts being tracked properly.


![Alarm set-up](assets/Week%200%20-%20Alarms.png)

11. Free tier service check
*  I checked service limits of specific services in my account under the free tier and how they could impact billing.
![Free tier check](assets/Week%200-Free%20tier.png)

*  I am almost using up my free tier services on EC2 for February. I have currently used 742hrs of 750 hrs so I'm opening up a support ticket to request a prolonged service limit.
  


   
## Homework Challenges
  - Created Architecture diagram on Napkins
  - ### AWSEventbridge
   I created a rule to hook up the Health Dashboard to SNS and send notification when there is a service health issue. Follow the steps [here.](https://docs.aws.amazon.com/health/latest/ug/cloudwatch-events-health.html)
   ![EventBridge set-up](assets/Week0-%20Eventbridge%20(2).png) 
   
  - ### Opened Support ticket for my EC2 instance
  I opened a suppoprt ticket because I was almost using up the free tier service for this month. I have used 742hrs of my 750hrs for this month. Check the steps [here.](https://docs.aws.amazon.com/awssupport/latest/user/create-service-quota-increase.html)
  
  - ### AWS Credits
   I got a $100 credit from the Mongodb AWS Marketplace event. 
 ![AWS Credits](assets/Week%200-%20Credits.png)
