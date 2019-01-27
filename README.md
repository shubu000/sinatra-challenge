REA Systems Engineer practical task
===================================
There are two ways of doing this

##1- Via Console

**Prerequisites**

To deploy this application on the server, you need:

AWS account

**Steps**

1   I used Amazon elastic bean stalk as a way to deploy the code to the cloud.

2   I logged into the console and selected elastic beanstalk

3   I simply created a new application, gave it a name

4   After this I created the environment via the wizard, I named the fields and uploaded a zip from my github.

After this beanstalk will create the environment.

To get the zip, click on the download button to get the zip.

**Finished result**

The working example is at http://13.236.19.152/
I have uploaded the beanstalk config onto github as REASinatrastable.cfg.yml

I also used codepipeline to setup automatic deployment from github.
In the pipeline, i used github as a source, codebuild as a building engine and use the previously created environment for deployment.


##2- Via CLI

**Prerequisites**

- GIT
- AWS eb cli

**Code**

Clone this repositry to your local drive via 
  
  git clone https://github.com/shubu000/sinatra-challenge

**Permissions**

Setup ebCLI with IAM user
  Make sure the user has these policies
    AWSElasticBeanstalkEnhancedHealth
    
    AWSElasticBeanstalkWebTier
    
    AWSElasticBeanstalkMulticontainerDocker
    
    AWSElasticBeanstalkService
    
    AWSElasticBeanstalkWorkerTier
    
    AWSElasticBeanstalkCustomPlatformforEC2Role

You would need 1 additional permission, i have attached the setting as autoscaling.json

**Elastic Beanstalk**

*Application*

To create the application, use
    
    eb init { application name }
    
choose a region suitable for you

Put REASinatrastable.cfg.yml into your GIT folder's beanstalk config folder,
  
  cp  REASinatrastable.cfg.yml /GIT PATH/.elasticbeanstalk/saved-config/REASinatrastable.cfg.yml 

where GIT PATH is where you have the git clone.

*Environment*

To create the environment, use the following command

    eb create { env-name } --cfg REASinatrastable.cfg.yml

Replace { env-name } with the name of the environment, take out the brackets.

Once it is deployed, you can access the web server via the EIP.

In this case, try http://13.238.206.41/
The results are identical


To keep this readme clean, i have attached further text files on how i come to these choices and what i had tried but did not work.

analysisandthoughts.txt - How i arrive at elastic beanstalk

Thank you!
