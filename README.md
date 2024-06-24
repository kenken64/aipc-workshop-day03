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
packer build build.pkr.hcl
```
