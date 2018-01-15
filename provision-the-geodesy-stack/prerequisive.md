# Configure through web console:

---

## IAM User & Key-pair

Create a IAM user,"geodesy";  also create a AWS key-pair "geodesy" in Web portal, keep the private key in the local disk as "geodesy.pem", for example, ~/.ssh/geodesy.pem.

It will be used when you need ssh access into the EC2 box \(Jump, OpenAM or etc\)

## API Access Key

While creating "geodesy" user, saving the ACCESS_KEY  and SECRETE_\_KEY in your local disk using the profile "geodesy". for more information, refer to AWSCLI

`[geodesy]`

`region=xxx`

`AWS_ACCESS_KEY_ID=xxx`

`AWS_SECRET_ACCESS_KEY=xxx`

It will be used by any AWS Cli commands to authenticate against AWS service endpoints, such as "aws ec2/ s3/ codedeploy/ cloudformation".

## Install following cli on your laptop:

---

* AWSCLI
* CredStash
* Amazonia
* Packer & Terraform

### **awscli**

Must do it first and run aws configured --profile geodesy.

\(details is omitted\)

### **credstash**:

either be installed inside virtualenv or system:

1. Obtain a local copy of Geodesy stack code.

```
#if you don't have commit access to GA github, you should fork Geodesy-web-service 
to your/your organization account first.

git clone <repo_of_geodesy_web_service>
cd Geodesy-Web-Services
git checkout -b master remotes/origin/master (because the default branch is "next")
# verify it matches all the commits as the remote master branch. i.e. git ls-remote show ...

# get hotfix of OpenAM bugs by Lazar.
git checkout -b openam-fix remotes/origin/determinsitive-fix
```

1. install credstash in virtualenv 

**note:** assuming you are using bash; otherwise, zsh/fish needs some alternation\)

```
$ cd <Geodesy-Web-Services>/aws
$ virtualenv -p path/to/python env
$ source env/bin/activate
(env) $ pip or pip3 install credstash
#You might need search google to fix some issues related to Crytography if your credstash is not happy.
$ credstash setup
...
# provide everything the same as you would for "aws configure --profile geodesy"; 
# both of application needs to talk to AWS API endpoints.
```

**Amazonia:**

```
$ cd geodesy-web-services/aws
$ virtualenv env
$ . env/bin/activate
$ python --version
Python 3.6.3
$ cd amazonia
$ (cd amazonia && pip install -r requirements.txt -e .)
$ ./deploy-infa.sh create dev
```



