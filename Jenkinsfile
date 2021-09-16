
pipeline {
	agent any
	stages {
		stage('Lint HTML') {
			steps {
				sh 'tidy -q -e ./app_CI_CD_pipeline/*.html'
			}
		}
		
		stage('Build Docker Image') {
			steps {
				withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]){
					sh '''  
						sudo docker build --file ./app_CI_CD_pipeline/Dockerfile -t davincizhao/capstone:$BUILD_ID .
					'''
				}
			}
		}

		stage('Push Image To Dockerhub') {
			steps {
				withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]){
					sh '''
						sudo docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
						sudo docker push davincizhao/capstone:$BUILD_ID
						echo $BUILD_ID
					'''
				}
			}
		}
		

		stage('Set current kubectl kubeconfig') {
			steps {
				withAWS(region:'us-west-1', credentials:'jenkins') {
					sh '''
						sudo kubectl config use-context arn:aws:eks:us-west-1:560967782130:cluster/capstonecluster 
					
					'''
				}
			}
		}

		
		stage('Deploy blue container') {
			steps {
				withAWS(region:'us-west-1', credentials:'aws_credential') {
					sh '''
						sudo kubectl apply -f ./app_CI_CD_pipeline/blue-ctler.json
					'''
				}
			}
		}
				
                stage('Deploy green container') {
                        steps {
                                withAWS(region:'us-west-1', credentials:'aws_credential') {
                                        sh '''
                                                sudo kubectl apply -f ./app_CI_CD_pipeline/green-ctler.json
                                        '''
                                }
                        }
                }

		
		stage('Create the service in the cluster, redirect to blue') {
			steps {
				withAWS(region:'us-west-1', credentials:'aws_credential') {
					sh '''
						sudo kubectl apply -f ./app_CI_CD_pipeline/blue-svc.json
					'''
				}
			}
		}
		stage('Wait user approve') {
                        steps {
                                input "Ready to redirect traffic to green?"
                               }
		
	        }

		stage('Create the service in the cluster, redirect to green') {
			steps {
				withAWS(region:'us-west-1', credentials:'aws_credential') {
					sh '''
						sudo kubectl apply -f ./app_CI_CD_pipeline/green-svc.json
					'''
				}
			}
		}
	}

}
