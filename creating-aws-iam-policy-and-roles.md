Create a role - codedeploy, it is supposed to be assumed by Codedeploy service:

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

Create a role - GeodesyWebServicesD-WebServerRole

This role is It will be used by EC2 instances \(Nat, Jump\), or by ASG Launch Configuration \(GeoServerAsgLc/WebServiceAsgLc/OpenAMAsgLc\) as their IamInstanceProfile to launch instances. The attachment of this role:





