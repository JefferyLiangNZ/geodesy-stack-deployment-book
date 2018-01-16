# CodeDeploy \(Role\) {#codedeploy-role}

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

# GeodesyWebServicesD-WebServerRole \(Role\) {#geodesywebservicesd-webserverrole}

which is used by EC2 instances \(Jump, Nat\), or AsgLaunchConfig \(OpenAMAsg, GeoserverAsg or WebservicesAsg\) as their IamInstanceProfile

There are 5 AWS Managed Role attached with Customer Role \(Credstash\_Reader\)

```
AmazonRDSFullAccess
AmazonS3FullAccess
AmazonEC2ReadOnlyAccess
AWSCodeDeployRole
AWSSNSFullAccess
```

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

---

# [Credstash\_Reader](https://console.aws.amazon.com/iam/home?#/policies/arn%3Aaws%3Aiam%3A%3A432193813149%3Apolicy%2FCredstash_Reader) \(self-defined Policy\) {#credstashreader-policy}

Firstly create a new policy as the following, name it as [Credstash\_Reader](https://console.aws.amazon.com/iam/home?#/policies/arn%3Aaws%3Aiam%3A%3A432193813149%3Apolicy%2FCredstash_Reader)![](/assets/FireShot Capture 011 - IAM Management Console - https___console.aws.amazon.com_iam_home_#_policies.jpg)

The content of Policy is copied out as:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "kms:Decrypt"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:kms:ap-southeast-2:432193813149:key/9244ea52-8465-44d4-85f6-4a23eb083075"
        },
        {
            "Action": [
                "dynamodb:GetItem",
                "dynamodb:Query",
                "dynamodb:Scan"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:dynamodb:ap-southeast-2:432193813149:table/credential-store"
        }
    ]
}
```

---

# CredstashReader \(Role\)

When creating that role, select "AWS Service" -&gt; "Lambda" for the step "Select type of trusted entity", then choose "Credstash\_Reader" to attach to the new role.

The content of role looks like:

```
{
    "Role": {
        "Description": "Allows Lambda functions to call AWS services on your behalf.", 
        "AssumeRolePolicyDocument": {
            "Version": "2012-10-17", 
            "Statement": [
                {
                    "Action": "sts:AssumeRole", 
                    "Effect": "Allow", 
                    "Principal": {
                        "Service": "lambda.amazonaws.com"
                    }
                }
            ]
        }, 
        "RoleId": "AROAIUO5ISJT5JXSZBHFM", 
        "CreateDate": "2018-01-12T03:03:29Z", 
        "RoleName": "CredstashReader", 
        "Path": "/", 
        "Arn": "arn:aws:iam::432193813149:role/CredstashReader"
    }
}
```



