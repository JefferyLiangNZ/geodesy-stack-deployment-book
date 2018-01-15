Building AMI  for web services

```
$ cd Geodesy-Web-Services/tree/master/aws/packer
$ cd ./geodesy-web-services
$ packer validate build.json
$ AWS_ACCESS_KEY=xxx AWS_SECRET_KEY=yyyyyyyy packer build ./build.json
#keep a note of what's the ami-id, it is a string similar to "ami-90fec3f3".
```

Building AMI for Geoserver

```
$ cd Geodesy-Web-Services/tree/master/aws/packer
$ cd ./geoserver_2.9.1
$ packer validate build.json
$ AWS_ACCESS_KEY=xxx AWS_SECRET_KEY=yyyyyyyy packer build ./build.json
```

Building AMI for OpenAM

```
$ cd Geodesy-Web-Services/tree/master/aws/packer
$ cd ./openam-13.5.0
$ packer validate build.json
$ AWS_ACCESS_KEY=xxx AWS_SECRET_KEY=yyyyyyyy packer build ./build.json
```

Note: Before run the command of packer build for "openam", make sure that the branch contains the openam-hotfix from previous steps. \(described in "pre-requsitive"\)

