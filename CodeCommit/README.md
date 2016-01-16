Creating a SSH key for CodeCommit using the AWS CLI
------------
###General

In order to go through this tutorial make sure that you already have configures the AWS CLI in your machine and that your IAM User have Full Access permission on CodeCommit and permission to upload SSH Public Keys for IAM users.


###Creating the Repository
```
aws codecommit create-repository --repository-name [YourRepoName]

#Example
aws codecommit create-repository --repository-name aws-developer-fundamentals
```


###Generating the SSH Key:

```
cd ~/.ssh
ssh-keygen
```

Follow the steps to create a key, you need to choose a name for it and either or not use a passphrase.

###Upload SSH Key to IAM

```
aws iam upload-ssh-public-key --user-name [IAM User name] --ssh-public-key-body "$(cat [Key name .pub])"

#Example:
aws iam upload-ssh-public-key --user-name codecommit --ssh-public-key-body "$(cat codecommit.pub)"
```

###Setting the config file

```
touch config
chmod 600 config
vim config
```
Insert this information into the **config** file:

```
Host git-codecommit.*.amazonaws.com
  User [SSHPublicKeyId]
  IdentityFile ~/.ssh/[Key name]
  
#Example:
  
Host git-codecommit.*.amazonaws.com
  User AWDLIJ12384O91K
  IdentityFile ~/.ssh/codecommit
```

###Testing

```
ssh git-codecommit.us-east-1.amazonaws.com
```

