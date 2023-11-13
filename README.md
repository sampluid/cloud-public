# cloud-public
# AWS Cloud Resume Challenge

This is my attempt at cloud resume challenge in AWS.
What is Cloud Resume Challenge? - [The Cloud Resume Challenge](https://cloudresumechallenge.dev/) is a multiple-step resume project which helps build and demonstrate skills fundamental to pursuing a career in Cloud. The project was published by Forrest Brazeal.


These are the AWS tools and programming languages I used to complete this project:

Stacks in CloudFormation - This is where I created all of the resources initially to start the process of hosting the website in AWS. I created the resources using AWS Vault and Powershell. AWS Vault was used to store my credentials in order to deploy these resources from templates via remote shell. This way, none of the resources had to be manually created via the AWS user interface. The resources created for this are listed below:

- AWS::Lambda::Function
- AWS::Lambda::Permission
- AWS::IAM::Role
- AWS::S3::Bucket
- AWS::ApiGateway::RestApi
- AWS::ApiGateway::Deployment
- AWS::ApiGateway::Stage

The templates I created can be found here - https://github.com/sampluid/Cloud-resume-challenge/tree/main/cloud-resume-challenge

Once I had the stack created, I used S3 Buckets to store the files that AWS used for my website. That included the HTML, CSS, and Javascript files for my resume. Those can be found here - https://github.com/sampluid/cloud-public/tree/main/resume

I then purchased a custom domain through Route53. I also generated SSL certificates and configured HTTPS to secure the website.  

I then used DynamoDB and Lambda to create the website counter that you can find at the bottom right of the resume website. DynamoDB is the database that Lambda references. Lambda allowed me to create an API using Python. You can find the source code I created here -  https://github.com/sampluid/Cloud-resume-challenge/blob/main/cloud-resume-challenge/Lambda-Python-api.py

To display the website counter, I used Javascript that the HTML file references. The Javascript code can be found here - https://github.com/sampluid/cloud-public/blob/main/resume/index.js

Finally, I setup CI/CD using my GitHub repository to automatically push changes to the website without having to access AWS at all. This involved creating a Yaml file and storing secret access keys within GitHub. That can be found here - https://github.com/sampluid/cloud-public/blob/main/.github/workflows/frontend-cicd.yaml

The next steps will be to setup DNSSEC to add additional security and to improve the HTML and CSS code to make the website appearance better. Although I did learn a lot of HTML and CSS, that was not the focus of this challenge so the website is pretty basic at this point in time 
