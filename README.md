# CI/CD for PHP Projects with AWS

Recently I learned how to create a Continuous Integration and Continuous Deployment [CI/CD] pipeline for any PHP based projects with all AWS services. This is what I am going to share with you all today.

AWS has multiple ways to create CI/CD for PHP based projects. Among them I am going to showcase 2 of them, one easy and one difficult!

Context:

PHP framework: Laravel [Latest Version]

AWS Service: CodeStar, CodePipeline, CodeCommit, ElasticBeanStalk, EC2, Auto Scaling Group, S3, RDS etc.

Other Service: Github

👉 Customized method: CodeCommit + Elastic BeanStalk + CodePipeline.

This is a custom made CI/CD for PHP based frameworks like Laravel. The key service is ElasticBeanStalk here. AWS Service configuration needs to be done in the same step after step mentioned. Like;

Please have a look on the solutions Architecture for the CI/CD pipeline:

![aws01](https://user-images.githubusercontent.com/47071968/178912771-7bd0fdc6-744f-43a6-a9f0-d5b1a989cd45.png)

=> First Create and configure CodeCommit or any other version control system like Github. I will use Github repo in this case:

![aws0202](https://user-images.githubusercontent.com/47071968/178913257-cc32bd72-61e8-445e-bd55-d908fa2b3a92.PNG)

=> Secondly configure Elastic BeanStalk with the desired environment settings and define PHP as the programming language.

![aws03](https://user-images.githubusercontent.com/47071968/178913553-7c0afbe5-1eb7-4a5b-8c01-bba06e531422.png)

Get the Elastic Beanstalk project but with an error on project status:

![aws04](https://user-images.githubusercontent.com/47071968/178913807-e9fbdde0-60d9-489d-8a75-e69a3b9df241.png)

Add these 2 IAM permissions to the role mentioned on the warning:

![aws05](https://user-images.githubusercontent.com/47071968/178914352-90e9e710-1e52-499c-b8dd-4173cf827a41.png)


This Warning will go away with an OK status! 😎
=> Now it's time to create the pipeline with the help of AWS CodePipeline service.

![aws06](https://user-images.githubusercontent.com/47071968/178914530-dbd9f4e5-6a87-4bee-ad3e-7b7ebefca0aa.png)

Next step add code source, here I am adding Github source. So for Github repo connection you will have to create a connection and install an AWS application in Github side and get the connection.
Select the correct repo and branch, leave everything else default.

![aws07](https://user-images.githubusercontent.com/47071968/178914780-75891bd2-5342-4461-af6d-96977ee93896.png)

Skip next build step as Elastic BeanStalk will take care of it.

![aws08](https://user-images.githubusercontent.com/47071968/178915212-e748a868-12a5-4490-8d50-8335b2b2fd6f.png)
![aws09](https://user-images.githubusercontent.com/47071968/178915321-73da9923-3a3a-4e51-8392-032fea7567c5.png)

Click next and complete the pipeline configuration details. It will take some time to complete the deployment pipeline.

![aws10](https://user-images.githubusercontent.com/47071968/178915595-2b0927d0-4198-4d1d-8d82-24d753376878.png)

Here you go with the fully automated CI/CD pipeline using github + Elastic Beanstalk + CodePipeline for any PHP frameworks like Laravel.
Let me tell you another easiest method to create this same pipelien without doing configuration for Elastic Beanstalk or creating any repo. Sounds cool right!
👉 Easiest method: AWS CodeStar 
With AWS CodeStar, you can create Laravel CI/CD pipeline in 3 min! I am not kidding at all. With a few clicks AWS CodeStar allows you to create an fully automated CI/CD using their predefined Cloudformation template.


CodeStar not only helps you create a robust CI/CD pipeline but also it has other awesome features like integrating IDEs, add team members, monitoring deployment error logs, track issues and many more. Out of the box features to have fully managed EC2 instances with preconfigured Auto Scaling Group to handle traffic and scale horizontally as per need.
Specially I love this feature of AWS to handle such a heavy lifting and save a lot of time for the server support and developers to focus more on coding. let's see things in action...

CodeStar Solutions Architecture:
![aws11](https://user-images.githubusercontent.com/47071968/178915926-db305443-9070-46e3-9a76-bd1f0d554b96.png)

AWS CodeStar supports more then 30 frameworks from almost all the common and most used programming languages.
![aws12](https://user-images.githubusercontent.com/47071968/178916086-97132bca-efe3-4799-b2b5-f9595b5e5d15.png)

From there choose your desired programming language and then choose framework template to go for next step to define server side configurations.
![aws13](https://user-images.githubusercontent.com/47071968/178916514-dbc4215e-608f-4f6b-b429-959a33046e69.png)

Nest step is to define code source for the CodeStar project as either CodeCommit or Github along with EC2 instance type, VPC, Subnet and EC2 Key Pair for the instance to configure.

![aws14](https://user-images.githubusercontent.com/47071968/178916680-ac79b4df-619a-46d0-8ac9-08aea22f1454.png)

Click Next and review all the configurations set up and complete creating your AWS CodeStar CI/CD pipeline for PHP Laravel project. It will take some time to complete the configuration. And after completion you will find your project listed like this and you can see your Repository, Pipeline and other features listed in one place.

![aws15](https://user-images.githubusercontent.com/47071968/178916892-3e2ebfd0-d5f7-4c58-bb0c-232494248c7b.png)
![aws16](https://user-images.githubusercontent.com/47071968/178917016-98e6906e-945f-471a-9391-cd8d2d66cd07.jpg)

Hope you find it useful and learned something new out of it. Please let me know if you have any other Solutions architecture for creating CI/CD with all AWS Services.
