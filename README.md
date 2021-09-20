# Capstone-cloud-deploy


## Propose and Scope the Project
- CI/CD tool platform: Jenkins,cloudformation,AWS,AWS Kubernetes as a Service
- Deployment strategy: Blue/green deployment.
- Container: Docker.
- Application: Nginx
- Repo: Github


## Tool-box server(Jenkins)
Tools:
- Docker,Container platform
- Jenkins,for CI/CD pipeline platform(JAVA base)
- kubectl,for Kubernetes cluster command line
- eksctl,for AWS Elastic Kubernetes Services command line
- awscli,for AWS  command line
.

## Repo Structure
There are Two branches [create_cluster] and [app_cicd]: 
- [create_cluster](https://github.com/davincizhao/Capstone-cloud-deploy/tree/create_cluster) for create infrastructure(EKS,Nodegroups) in AWS, 
- [app_cicd] for test code, build app deploy app to EKS,expose service.
- prepare_jeniks_tools.sh, in create_cluster branch for prepare install jenkins and other relative tools, like docker,tidy..
