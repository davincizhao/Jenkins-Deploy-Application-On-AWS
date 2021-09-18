
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
						  docker build --file ./app_CI_CD_pipeline/Dockerfile -t davincizhao/testcapstone:$BUILD_ID -t davincizhao/testcapstone:latest  .
					'''
				}
			}
		}

		stage('Push Image To Dockerhub') {
			steps {
				withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]){
					sh '''
						  docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
						  docker push davincizhao/testcapstone:latest
						  echo $BUILD_ID
					'''
				}
			}
		}
		

		stage('Set current kubectl kubeconfig') {
			steps {
				withAWS(region:'us-west-2', credentials:'aws_credential') {
					sh '''
						  aws --region us-west-2 eks update-kubeconfig --name cap99 
					
					'''
				}
			}
		}

		stage('test config') {
			steps {
				withAWS(region:'us-west-2', credentials:'aws_credential') {
					sh '''
						kubectl get svc 
					
					'''
				}
			}
		}

		
		stage('Deploy blue container') {
			steps {
				withAWS(region:'us-west-2', credentials:'aws_credential') {
					sh '''
						  kubectl apply -f ./app_CI_CD_pipeline/blue-ctler.json
					'''
				}
			}
		}
				
                stage('Deploy green container') {
                        steps {
                                withAWS(region:'us-west-2', credentials:'aws_credential') {
                                        sh '''
                                                  kubectl apply -f ./app_CI_CD_pipeline/green-ctler.json
                                        '''
                                }
                        }
                }

		
		stage('Create the service in the cluster, redirect to blue') {
			steps {
				withAWS(region:'us-west-2', credentials:'aws_credential') {
					sh '''
						  kubectl apply -f ./app_CI_CD_pipeline/blue-svc.json
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
				withAWS(region:'us-west-2', credentials:'aws_credential') {
					sh '''
						  kubectl apply -f ./app_CI_CD_pipeline/green-svc.json
					'''
				}
			}
		}
	}

}
