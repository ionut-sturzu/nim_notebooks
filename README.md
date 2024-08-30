This playbook is used to interact with models deployed using NVIDIA NIMs. It uses a Gradio interface to ask questions to the model.

## Prerequisites

1. The `model_base_url` should be changed to reflect the name of the service in Kubernetes. To get the service name, first connect to the operator instance:
```
ssh -o ProxyCommand='ssh -W %h:%p opc@bastion_public_ip' opc@operator_private_ip
```
Once you are logged into the operator, list all the services:
```
k get svc
```
Retrieve the name of the service for your NIM deployment and replace it under model_base_url like this: model_base_url = "http://kubernetes_servicename/v1"

2. Model Name:
In the get_response_from_model function, replace the model name with the name of your model:
```
model="meta/llama3-8b-instruct"
```

## How to Run

To run it, first execute the initial cell of code to install the required Python packages and restart the kernel. After that, run the second cell, which will spin up a Gradio interface from where questions can be asked to the model.

