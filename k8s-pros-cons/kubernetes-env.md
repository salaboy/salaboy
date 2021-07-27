# Pros & Cons Kubernetes Environments

This file contains Pros & Cons for different Kubernertes environments.

## Local

| Pros  | Cons |
| ------------- | ------------- |
| Lightweight  | It is not a real cluster  |
| Fast to get started  | It behaves differently  |
| Good for testing | Reduced hardware to run workloads |
| Local development| Download containers to your local environment |
| Good for running small applications | |

Options: 
- [Minikube]()
- [KIND]()
- [K3s]()

## On-Prem

| Pros  | Cons |
| ------------- | ------------- |
| Real cluster on top of real hardware,  | It requires you to have hardware available  |
| It behave closer to how a production cluster  | It requires a mature operation team  |
| Remote environment for Development | Difficult to scale, compared to Cloud Providers |
| | It might lack features such as specific networking capabilties or special hard drives for storage |

Options: 
- [VMware Tanzu]()
- [Red Hat OpenShift]()


## Cloud Provider

| Pros  | Cons |
| ------------- | ------------- |
| Fully-fledged clusters  | Difficult to estimate cost  |
| Easy to scale and manage  | Cloud Provider specific expertise required  |
| You don't need to deal with hardware | Possible vendor lock-in |
| Other services provided besides Kubernetes | You might need a big credit card |
| Pay as you go, use free trials | |

Options: 
- [Google Cloud Platform + GKE]
- [AWS + EKS]
- [Azure + AKS]
- [Linode + LKE]

[Free trials Here](https://github.com/learnk8s/free-kubernetes) 


