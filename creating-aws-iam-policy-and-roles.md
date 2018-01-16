# CodeDeploy \(Role\)

| iam list-attached-role-policies --role-name CodeDeploy |
| :--- |


```
{
    "AttachedPolicies": [
        {
            "PolicyName": "AWSCodeDeployRole", 
            "PolicyArn": "arn:aws:iam::aws:policy/service-role/AWSCodeDeployRole"
        }
    ]
}
```

![](/assets/FireShot Capture 008 - IAM Management _ - https___console.aws.amazon.com_iam_home_#_roles_CodeDeploy.jpg)it is supposed to be assumed by Codedeploy service, the only attachment \("policy"\) is AWSCodeDeployRole.

| iam get-policy --policy-arn arn:aws:iam::aws:policy/service-role/AWSCodeDeployRole |
| :--- |


```
{
    "Role": {
        "Description": "Allows CodeDeploy to call AWS services such as Auto Scaling on your behalf.", 
        "AssumeRolePolicyDocument": {
            "Version": "2012-10-17", 
            "Statement": [
                {
                    "Action": "sts:AssumeRole", 
                    "Principal": {
                        "Service": "codedeploy.amazonaws.com"
                    }, 
                    "Effect": "Allow", 
                    "Sid": ""
                }
            ]
        }, 
        "RoleId": "AROAIEGQKDXB2PQZBB5XU", 
        "CreateDate": "2018-01-09T22:54:37Z", 
        "RoleName": "CodeDeploy", 
        "Path": "/", 
        "Arn": "arn:aws:iam::432193813149:role/CodeDeploy"
    }
}
```

Note: This role's Trusted entities should be **codedeploy.amazonaws.com**



---

# GeodesyWebServicesD-WebServerRole \(Role\)

which is used by EC2 instances \(Jump, Nat\), or AsgLaunchConfig \(OpenAMAsg, GeoserverAsg or WebservicesAsg\) as their IamInstanceProfile

![](/assets/FireShot Capture 009 - IAM Management Console_ - https___console.aws.amazon.com_iam_home.jpg)



| iam get-role --role-name GeodesyWebServicesD-WebServerRole |
| :--- |
| **iam list-attached-role-policies --role-name GeodesyWebServicesD-WebServerRole** |

```
{
    "Role": {
        "Description": "Allows EC2 instances to perform all functions on behalf of owner", 
        "AssumeRolePolicyDocument": {
            "Version": "2012-10-17", 
            "Statement": [
                {
                    "Action": "sts:AssumeRole", 
                    "Effect": "Allow", 
                    "Principal": {
                        "Service": "ec2.amazonaws.com"
                    }
                }
            ]
        }, 
        "RoleId": "AROAIRZXH5XTLPYFW7UCS", 
        "CreateDate": "2018-01-08T21:45:31Z", 
        "RoleName": "GeodesyWebServicesD-WebServerRole", 
        "Path": "/", 
        "Arn": "arn:aws:iam::432193813149:role/GeodesyWebServicesD-WebServerRole"
    }
}

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



