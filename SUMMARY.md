# Summary

* [Introduction](README.md)
* [1. Provision the geodesy stack](provision-the-geodesy-stack.md)
  * [Prerequisive](provision-the-geodesy-stack/prerequisive.md)
  * [Steps](provision-the-geodesy-stack/steps.md)
    * [Creating AMI in the AWS accout](creating-ami-in-the-aws-accout.md)
    * [Creating/importing a certificate into Certificate Manager](creatingimporting-a-certificate-into-certificate-manager.md)
    * [Creating AWS IAM policy & roles](creating-aws-iam-policy-and-roles.md)
    * [Preparing the CFN template](preparing-the-cfn-template.md)
  * Validations
* [2. Config and deploy OpenAM](deploy-config-and-code-into-openam-asg.md)
  * [Steps](deploy-config-and-code-into-openam-asg/steps.md)
    * [Reconfigure the deployment code](deploy-config-and-code-into-openam-asg/steps/reconfigure-the-deployment-code.md)
    * [Configure OpenAM Server and backup](deploy-config-and-code-into-openam-asg/steps/configure-openam-server-and-backup.md)
  * Validations
* [3. Deploy Webservice & GeoServer](deploy-config-and-code-into-webservice-and-geoserver-asg.md)
  * Steps
    * Compile & build source code 
    * Adaption of codedeploy code
  * Validations
* [4. Deploy GNSS-Site-manager and CloudFront](deploy-gnss-site-manager-in-s3-and-config-cloudfront.md)
  * [Steps](deploy-gnss-site-manager-in-s3-and-config-cloudfront/steps.md)
  * [Preparations](deploy-gnss-site-manager-in-s3-and-config-cloudfront/preparations.md)
* [5. Deploy Converter Lambda Func](deploy-gnss-site-manager-in-s3-and-config-cloudfront/preparetions.md)
  * [Steps](deploy-gnss-site-manager-in-s3-and-config-cloudfront/preparetions/steps.md)
    * [S3 Buckets & Terraform HCL code](deploy-gnss-site-manager-in-s3-and-config-cloudfront/preparetions/steps/s3-buckets-and-terraform-hcl-code.md)
    * [Run Terraform](deploy-gnss-site-manager-in-s3-and-config-cloudfront/preparetions/steps/run-terraform-config.md)
  * [Validations](deploy-gnss-site-manager-in-s3-and-config-cloudfront/preparetions/validations.md)

