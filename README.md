REA Systems Engineer practical task
===================================

To deploy this application on the server, you need:
AWS account

I used Amazon elastic bean stalk as a way to deploy the code to the cloud.
I logged into the console and selected elastic beanstalk
I simply created a new application, gave it a name
After this I created the environment via the wizard, I named the fields and uploaded a zip from my github.
After this beanstalk will create the environment.

So if you want to repeat this, click on the download button to get the zip.

The working example is at http://13.236.19.152/
I have uploaded the beanstalk config onto github as REASinatrastable

I also used codepipeline to setup automatic deployment from github.
In the pipeline, i used github as a source, codebuild as a building engine and use the previously created environment for deployment.

To keep this readme clean, i have attached further text files on how i come to these choices and what i had tried but did not work.

analysisandthoughts.txt - How i arrive at elastic beanstalk
Thank you!
