03 - CodeDeploy
----------------------

###Creating a new Deployment with the AWS CLI

First upload the source codes as a **.zip** file

```
aws deploy push --application-name [ApplicationName] --s3-location s3://[BucketName]/[FileName].zip --source [PathToSource]

#Example:

aws deploy push --application-name my-app --s3-location s3://app-revision/bundle.zip --source .
```

AWS will spit out something like this

```
aws deploy create-deployment --application-name my-app --s3-location bucket=app-revision,key=bundle.zip,bundleType=zip,eTag="e0d168a660327969b049c253ab85ea81" --deployment-group-name <deployment-group-name> --deployment-config-name <deployment-config-name> --description <description>
```

Just Change the last 3 paramentes and submit the command:

```
aws deploy create-deployment --application-name my-app --s3-location bucket=app-revision,key=bundle.zip,bundleType=zip,eTag="e0d168a660327969b049c253ab85ea81" --deployment-group-name dev --deployment-config-name CodeDeployDefault.AllAtOnce --description "description"
```
AWs will reply with an Deployment ID, you can check the status of a deployment by typing:

```
aws deploy get-deployment --deployment-id [DeplymentId]

#Example:

aws deploy get-deployment --deployment-id d-4TEIBW5ED
```