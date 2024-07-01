## AIPC Workshop Day 3

## Install packer on ubuntu 20.04 x86

```
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
```

````
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
````

```
sudo apt-get update && sudo apt-get install packer
```

## Initialize packer project

```
packer init config.pkr.hcl
```

## Build the packer golden image
```
packer build --var do_token=${DO_PAT} .
```

## Terraform provisioning

```
terraform init
```

```
terraform plan -var "do_token=${DO_PAT}" -var "ssh_private_key=/root/.ssh/id_rsa" -var "cs_password=password123456" -var "cs_domain=test"
```

```
terraform apply --auto-approve-var "do_token=${DO_PAT}" -var "ssh_private_key=/root/.ssh/id_rsa" -var "cs_passwword=password123456" -var "cs_domain=test"
```
