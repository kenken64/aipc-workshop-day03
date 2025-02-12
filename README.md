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

Under the build folder run the following commands 

```
packer init config.pkr.hcl
```

## Build the packer golden image
```
packer build --var DO_token=${DO_PAT} .
```

## Terraform provisioning


Install terraform 

```
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

```
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```
```
sudo apt update && sudo apt install terraform
```
Check the terraform version

```
terraform --version
```


Install Ansible on the Ubuntu instance

```
sudo apt-add-repository ppa:ansible/ansible

sudo apt update

sudo apt install ansible-core
```

Verify the ansible version

```
ansible --version
```



Under the deploy folder run the following commands 

```
terraform init
```

```
terraform plan -var "DO_token=${DO_PAT}" -var "ssh_priv_key=/root/.ssh/id_rsa" -var "code_server_password=password123456"

terraform apply --auto-approve -var "DO_token=${DO_PAT}" -var "ssh_priv_key=/root/.ssh/id_rsa" -var "code_server_password=password123456"
```


