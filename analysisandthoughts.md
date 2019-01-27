Before I started explaining what I did, I just want to thank you all for forcing me to learn how to deploy a server on AWS. 
Prior to this challenge, i had never:
-Deployed a server on AWS
-Read Ruby
-Started/Forked a github repo
So thank you!

Analysis phase 1 - Application
Before I deployed the application, I read the code on github to ascertain what is the application.
I can tell that it is a simple web server (Sinatra) displaying "helloworld" and the language is Ruby.

I then loaded the code onto a standard amazon VM (vanilla EC2 instance), to see what is needed to manually deploy the code.
I identified the components that I would need to install.


I then used codebuild to see whether there are issues with the app. 
I added the requried lines into the buildspec.yml and proceed to figure out how to deploy it.
I only needed the server to grab sinatra via gem since it is a ruby machine.
I then made the script run in the background, otherwise it would hold up build process

Analysis phase 2 - deployment platform
My first instinct is to roll a VM, I had done that a  number of times before, however since the instruction was to create code/config that is repeatable
I cannot simply send an image of a VM.
Seeing that this application only display text, I tried to use the most minimalist platform, lambda.
It is also possible to use just an EC2 instance to deploy this code.
Lastly I found beanstalk, but before that, this was all the things that i tried, none of them worked

Trial and Error phase

-AWS Lambda
I thought AWS Lambda is the most appropriate as the server is quite simple. 
However, I tried running it by itself or with code deploy, didn't work.
I searched for sinatra aws lambda on google, and i was able to find someone's sample code on github
I forked it and tried to follow the each command, however I got an unknown type error with AWS CLI


-AWS Codedeploy EC2
Having never to used this before, I found an example of deploying an application on EC2 via github.
I followed each step on the tutorial, however I am always greeted with an error about user roles.
I granted all codedeploy roles to the user as well as read only acess to s3, but that was not working.

-AWS elastic beanstalk - load balancer
I had expereienced a timeout on the webserver a few times, so i wanted to add a load balancer to make it highly available, however i was never able to reach the server despite typing in the ip address. This is something that can be improved in the future.

- IAM roles and security

I tried to minimise the amount of roles assigned to any user. However when permission errors occurs, i just have to keep adding the roles. As of my current solution, I think that the roles can be reduced to become more granular, but that can be a further improvement later on.

Future improvements
~~Working eb create command to create the stack via CLI~~
Solve load balancing and add/force https for security
I have disabled SSH for now for security, but that can be modified later for more advanced usage
Trim security roles
