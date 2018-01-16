# Codedeploy Role

![](/assets/FireShot Capture 008 - IAM Management _ - https___console.aws.amazon.com_iam_home_#_roles_CodeDeploy.jpg)it is supposed to be assumed by Codedeploy service, the only attachment \("policy"\) is AWSCodeDeployRole.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "",
      "Effect": "Allow",
      "Principal": {
        "Service": "codedeploy.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
```

this role's Trusted entities should be **codedeploy.amazonaws.com**

Create a role - GeodesyWebServicesD-WebServerRole, which is used by EC2 instances \(Jump, Nat\), or AsgLaunchConfig \(OpenAMAsg, GeoserverAsg or WebservicesAsg\) as their IamInstanceProfile



| aws iam list-attached-role-policies --role-name GeodesyWebServicesD-WebServerRole |
| :--- |


```
{
    "AttachedPolicies": [
        {
            "PolicyName": "AmazonRDSFullAccess", 
            "PolicyArn": "arn:aws:iam::aws:policy/AmazonRDSFullAccess"
        }, # AWS Managed Role
        
        {
            "PolicyName": "AmazonS3FullAccess", 
            "PolicyArn": "arn:aws:iam::aws:policy/AmazonS3FullAccess"
        }, 
        
        {
            "PolicyName": "AmazonEC2ReadOnlyAccess", 
            "PolicyArn": "arn:aws:iam::aws:policy/AmazonEC2ReadOnlyAccess"
        }, 
        
        {
            "PolicyName": "AWSCodeDeployRole", 
            "PolicyArn": "arn:aws:iam::aws:policy/service-role/AWSCodeDeployRole"
        }, # this role is service role, it is supposed to be used by a AWS Service (Trustee)
        
        {
            "PolicyName": "Credstash_Reader", 
            "PolicyArn": "arn:aws:iam::432193813149:policy/Credstash_Reader"
        }, 
        {
            "PolicyName": "AmazonSNSFullAccess", 
            "PolicyArn": "arn:aws:iam::aws:policy/AmazonSNSFullAccess"
        }
    ]
}

```



