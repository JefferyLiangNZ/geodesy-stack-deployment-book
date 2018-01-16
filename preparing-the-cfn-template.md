## **Editing the infra-basic.yml, infra-defaults.yml**

1. [ ] update the ami id
2. [ ] update the CIDR for VPC, public subnet, private subnet
3. [ ] update the Jump SG's CIDR \(original one is for GA's usage\)
4. [ ] update the Certificate Manager ARN
5. [ ] update the Domain name from "geodesy.ga.gov.au" to choosen domain name \(meaningful to your org\)





## **Provision the infra.json file;**

```
./deploy-infa.sh create dev
or 
./deploy-infra.sh update dev 

#if the target env is not dev, you should choose test or prod as the last para

```

## Run the CFN wrapper script;



