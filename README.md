# Capstone-cloud-deploy


## Step 1: Propose and Scope the Project
- CI/CD tool platform: Jenkins,cloudformation,AWS
- Deployment strategy: Blue/green deployment.
- Container: Docker.
- Application: Ngix
- Repo: Github
## Step 2: Use Jenkins implement blue/green deployment.
- create Jenkins master box and install the plugins.
-[Install Jenkins and login Jenkins](https://github.com/davincizhao/Jenkins_Pipelines_on_AWS/blob/master/README.md)
- Install epel
```
sudo amazon-linux-extras install epel
```
- Install git,tidy,docker
Enable docker daemon and allow jenkins to connect to docker engine.
'''
systemctl start docker
chown jenkins /var/run/docker.sock
'''

## Step 3: Pick AWS Kubernetes as a Service.
- Use Ansible or CloudFormation to build the Kubernetes Cluster.


## Step 4: Build your pipeline
- Construct pipeline with GitHub repository.
- Set up all the steps that your pipeline will include.
- Configure a deployment pipeline.
- include Dockerfile/source code in the Git repository.
- Include with Linting.
## Step 5: Test your pipeline
- Perform builds on your pipeline.

## Repo Structure
There are Two branches [create_cluster] and [app_cicd]: 
- one for create infrastructure(EKS,Nodegroups) in AWS, 
- another for test code, build app deploy app to EKS,expose service.
- prepare_jeniks_tools.sh, in create_cluster branch for prepare install jenkins and other relative tools, like docker,tidy..
