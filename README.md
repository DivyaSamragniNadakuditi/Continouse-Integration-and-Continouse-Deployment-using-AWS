# Continouse-Integration-and-Continouse-Deployment-using-AWS
Continuous Integration/ Continuous Development / Continuous Deployment these are the latest buzz words and extremely important areas for any Technological companies. It enables teams to build, test and release software at a faster rate and in a continuous fashion. CI/CD removes manual tasks where possible by  automating everything.  So adopting seamless and automatic deployment can help any organization save lot of time in this repetitive work and help the organization to have people concentrate more on architecture/design/development and less on  build/deployment .
 
In this project, we will setup continuous integration and continuous delivery (CI/CD) pipeline on AWS.  We will automate software delivery process, such as initiating automatic builds and then deploying to Amazon EC2 instances. We will use AWS CodePipeline, a service that builds, tests, and deploys code every time there is a code change, based on the release process models we define. Use CodePipeline to orchestrate each step in the release process. As part of project, we will architect other AWS services like S3, EC2, ECR, DynamoDB, CloudWatch, CloudTrail, SNS into and after CodePipeline to complete our software delivery process.


We can implement this project using the scalability and Automation features of the AWS Services.

<h2> Introduction </h2>
Continuous Integration in software development practice is where engineers  integrate the work that work very frequently. Once the code is integrated it then verifies it to ensure that the integrated code has not introduced any errors or bugs. The CI software is degraded with the source code repositories directly so, it allows in detection of changes as developers commit it. 

Continuous Delivery or Continuous deployment aims to building, testing and releasing software faster frequently. CI/CD pipeline is basically a set of steps that a code change has to go through.

In this project, we use a PHP web application that uses a  MySQL database. This code is modified using Cloud9 . We deploy the application in Elastic Beanstalk and use Codepipeline which is deployed using Git where we make the changes to the code. Below figure 1 shows the architecture of the project.

 
Figure 1: Architecture of the project

We further use AWS CloudWatch to generate the alerts of the applications health.


<h2> Implementation </h2>

List of All the services used:
•	Github.
•	AWS ElasticBeanstalk.
•	AWS Codepipeline.
•	AWS RDS.
•	AWS S3.
•	AWS Lambda.
•	AWS CloudWatch.

PHP Web Application Changes:
Firstly, we downloaded the PHP Application, initialize and pull all the dependencies. We further set environment variables. These are used to configure options. We add them to elastic beanstalk, this variable is used to determine what stage the application is in Development stage, Beta stage, production stage. We also use these variables to store database credentials. We commit all the code into GitHub Repository.

Deploy Project: Setting up AWS Elastic Beanstalk & RDS:
We will now deploy the application into Elastic Beanstalk. We will have builder and production stages. We will create a web application and configure the options before creation.


<h2> Screenshots of the project </h2>

 
Figure 2:Creating the Elastic Beanstalk Application.

We further add the database configurations as shown in figure 3.

 
Figure 3: Database configuration while creating an Elastic Beanstalk Application.
This should launch a sample application as we did not deploy our application. Figure 4 is the screenshot of the application launched.

 
Figure 4: Sample Application Launched in AWS Elastic Beanstalk

Now we will zip the code files and upload it to the Elastic Beanstalk Application. After Uploading, it will automatically deploy the Elastic Beanstalk Application. After the Deployment is completed, it will show the Application Environment as in Figure 5.

 
Figure 5: Health Status of Elastic Beanstalk environment after deploying the PHP Web Application.

When you click on the url available in the Elastic Beanstalk Environment, the following application Page should open as shown in Figure 6.

 
Figure 6: PHP Web Application launched on AWS ELastic Beanstalk.
We use Elastic Beanstalk extensions to run custom scripts. We then use the same procedure to add a new environment called Production to the Application created in Beanstalk. We use the same procedure like we created the Beta Application. In the versions section of Elastic Beanstalk, you can check the versions of code deployed into the Beanstalk. Figure 7 shows the different versions of code deployed.

 
Figure 7: Application Versions of Code deployed in Elastic Beanstalk.

Setting a CI/CD pipeline using AWS CodePipeline:
We first commit all the code in Github. Below is the link of the code in Github.
https://github.com/DivyaSamragniNadakuditi/fuzzy-telegram

 
Figure 8: Code in Github.

Now Create a new Codepipeline. Figure 9 shows the creation of new pipeline for our Application.
 
Figure 9 : Pipeline Creation for our Application.

Also set the Deployment to Elastic Beanstalk.
 
Figure 10: Source Provider details

 

Webhooks to detect deployment changes: -

For Github, we have used default system which is webhooks to recognize the changes made in Github code. Webhooks is one of the powerful ways to analyses and import the changes in cloud integrations. Web is event system

Webhooks are tightly integrated with Particle's event system. Devices have the ability to both publish events to the Particle cloud, as well as subscribe to events from the cloud.
A webhook listens for a specific event published by a device. When this event is published, the webhook triggers a web request to a URL on the web. The request sent by the webhook can include information about the event, such as its name as well as any data included when the event was published.



 
Figure 11: Deployment details

Below are the Figures of the Codepipeline Created Build and Deployed.

 
Figure 12: Codepipeline Successfully Build.

 
Figure 13: Deployment Successful.

We further add a stage called Production.
 
Figure 14: Adding new stage called Production




We have added cloud watch, to analyses the health of deployed Elastic Beans stalk environments and SNS notifications. Also this logs are stored in S3 bucket.
 
Fig 14. Adding Lambda function to check the health status of ElasticBeanstalk.
 
Fig 15. This is an email notification sent to client.


Conclusion: we have successfully implemented DevOps: Continuous Integration(CI) and Continuous Deployment(CD) using AWS CodePipeline & AWS Elastic Beanstalk

