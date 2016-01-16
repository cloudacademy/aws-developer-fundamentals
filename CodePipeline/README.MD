04 - CodePipeline
-------------------


###Launching instances for the new Deployment Group

Use one of the scripts below, depeding on the region that you are using, to launch new instances for our Deployment group

- http://s3.amazonaws.com/aws-codedeploy-us-east-1/templates/latest/CodeDeploy_SampleCF_Template.json (for the US East (N. Virginia) region)
- http://s3-us-west-2.amazonaws.com/aws-codedeploy-us-west-2/templates/latest/CodeDeploy_SampleCF_Template.json (for the US West (Oregon) region)
- http://s3-eu-west-1.amazonaws.com/aws-codedeploy-eu-west-1/templates/latest/CodeDeploy_SampleCF_Template.json (for the EU (Ireland) region)
- http://s3-eu-central-1.amazonaws.com/aws-codedeploy-eu-central-1/templates/latest/CodeDeploy_SampleCF_Template.json (for the EU (Frankfurt) region)
- http://s3-ap-southeast-1.amazonaws.com/aws-codedeploy-ap-southeast-1/templates/latest/CodeDeploy_SampleCF_Template.json (for the Asia Pacific (Singapore) region)
- http://s3-ap-southeast-2.amazonaws.com/aws-codedeploy-ap-southeast-2/templates/latest/CodeDeploy_SampleCF_Template.json (for the Asia Pacific (Sydney) region)
- http://s3-ap-northeast-1.amazonaws.com/aws-codedeploy-ap-northeast-1/templates/latest/CodeDeploy_SampleCF_Template.json (for the Asia Pacific (Tokyo) region)


###Launching an Instance with Jenkins

Launch a new instance and on step 2, insert this info into the UserData field.

```
#!/bin/bash
yum install -y java git wget ruby rubygems
gem install bundle
gem install rake
wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
yum install -y jenkins
service jenkins start
chkconfig jenkins on
```
###Configuring Jenkins

Execute shell command for Development:

	sed -i 's/deploymentGroup/Development/g' index.html

Execute shell command for Production:

	sed -i 's/deploymentGroup/Development/g' index.html


