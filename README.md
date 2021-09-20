# Capstone-cloud-deploy


## Propose and Scope the Project
- CI/CD tool platform: Jenkins,cloudformation,AWS,AWS Kubernetes as a Service(EKS)
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
- [app_cicd](https://github.com/davincizhao/Capstone-cloud-deploy/tree/app_cicd) for test code, build app deploy app to EKS,expose service.
- prepare_jeniks_tools.sh, in [create_cluster] branch for prepare install jenkins and other relative tools, like docker,tidy into Tool-box server

## Prepare Credential of AWS and Dockerhub
- Create user and add EKS permission into this user,save this credential in Jenkins, so that Jenkins can act as user to create EKS.
- Create keypair for login tool-box server(Jenkins) EC2 in AWS.
- Save dockerhub username and password in Jenkins, so that Jenkins can push docker image to dockerhub.

## Screenshot of project
### ss1_setup_jenkins.png
![ss1_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss1_setup_jenkins.png)

### ss2_setup_jenkins.png
![ss2_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss2_setup_jenkins.png)

### ss3_setup_jenkins.png
![ss3_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss3_setup_jenkins.png)

### ss4_setup_jenkins.png
![ss4_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss4_setup_jenkins.png)

### ss5_setup_jenkins.png
![ss5_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss5_setup_jenkins.png)

### ss6_setup_jenkins.png
![ss6setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss6_setup_jenkins.png)

### ss7_setup_jenkins.png
![ss7_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss7_setup_jenkins.png)

### ss8_setup_jenkins.png
![ss8_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss8_setup_jenkins.png)

### ss9_setup_jenkins.png
![ss9_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss9_setup_jenkins.png)

### ss10_setup_jenkins.png
![ss10_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss10_setup_jenkins.png)

### ss11_setup_jenkins.png
![ss11_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss11_setup_jenkins.png)

### ss12_setup_jenkins.png
![ss12setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss12_setup_jenkins.png)

### ss13_setup_jenkins.png
![ss13_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss13_setup_jenkins.png)

### ss14_setup_jenkins.png
![ss14_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss14_setup_jenkins.png)

### ss15_setup_jenkins.png
![ss15_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss15_setup_jenkins.png)

### ss16_setup_jenkins.png
![ss16_setup_jenkins.png](https://github.com/davincizhao/Capstone-cloud-deploy/blob/master/screenshots/ss16_setup_jenkins.png)
