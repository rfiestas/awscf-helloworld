# awscf-helloworld
aws cloud formation python helloworld test

## Description

Initial version, work with python-helloworld 0.0 , 0.1 , 0.2_FAIL

## Parameters
**KeyName**: credenciales aws (obligatorio)
**InstanceType**: por defecto t2.micro (opcional)
**SSHLocation**: habilita el puerto 22 hacia la red deseada.  (opcional)
**AplicationRepo**: por defecto https://github.com/rfiestas/nodejs-helloworld.git  (opcional)
**Tag**: aplica el tag / version deseada , por defecto 0.0 (opcional)
 
## Create stack
```
aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name helloworld --template-body file://awscf-helloworld.json --parameters  ParameterKey=KeyName,ParameterValue=helloworld  ParameterKey=Tag,ParameterValue="0.0"
```
## Wait and check

```
aws cloudformation wait stack-create-complete --stack-name helloworld
aws cloudformation describe-stacks --stack-name helloworld --output table
```
 
## Upgrade to 0.1 version

```
aws cloudformation update-stack --capabilities CAPABILITY_IAM --stack-name helloworld --template-body file://awscf-helloworld.json --parameters  ParameterKey=KeyName,ParameterValue=helloworld  ParameterKey=Tag,ParameterValue="0.1"
``` 

## Upgrade to 0.2_Fail version and rollback to previows

```
aws cloudformation update-stack --capabilities CAPABILITY_IAM --stack-name helloworld --template-body file://awscf-helloworld.json --parameters  ParameterKey=KeyName,ParameterValue=helloworld  ParameterKey=Tag,ParameterValue="0.2_FAIL"
``` 
