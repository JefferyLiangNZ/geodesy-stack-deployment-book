

# Codedeploy Role![](/assets/FireShot Capture 008 - IAM Management _ - https___console.aws.amazon.com_iam_home_#_roles_CodeDeploy.jpg)

![](/assets/FireShot Capture 008 - IAM Management _ - https___console.aws.amazon.com_iam_home_#_roles_CodeDeploy.jpg)Create a role - codedeploy, it is supposed to be assumed by Codedeploy service:

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

