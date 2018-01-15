## IAM User & Key-pair

Create a IAM user,"geodesy";  also create a AWS key-pair "geodesy" in Web portal, keep the private key in the local disk as "geodesy.pem", for example, ~/.ssh/geodesy.pem.

It will be used when you need ssh access into the EC2 box \(Jump, OpenAM or etc\)

## API Access Key

While creating "geodesy" user, saving the ACCESS_KEY  and SECRETE_\_KEY in your local disk using the profile "geodesy". for more information, refer to AWSCLI

`[geodesy]`

`region=xxx`

`CESS_KEY_ID=xxx`

`AWS_SECRET_ACCESS_KEY = xxx`

It will be used by any AWS Cli commands to authenticate against AWS service endpoints, such as "aws ec2/ s3/ codedeploy/ cloudformation".

