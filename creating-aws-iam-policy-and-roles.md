# CodeDeploy \(Role\)

| aws iam list-attached-role-policies --role-name CodeDeploy |
| :--- |


```
aws iam get-policy --policy-arn arn:aws:iam::aws:policy/service-role/AWSCodeDeployRole


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

this role's Trusted entities should be **codedeploy.amazonaws.com**

# GeodesyWebServicesD-WebServerRole \(Role\)

which is used by EC2 instances \(Jump, Nat\), or AsgLaunchConfig \(OpenAMAsg, GeoserverAsg or WebservicesAsg\) as their IamInstanceProfile

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



