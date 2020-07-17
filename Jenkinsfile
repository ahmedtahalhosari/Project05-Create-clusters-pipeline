pipeline {
	agent any
	stages {

		stage('Create kubernetes cluster') {
			steps {
				withAWS(region:'us-east-2', credentials: 'aws-static') {
					sh '''
						eksctl create cluster \
						--name capstone.cluster \
						--version 1.14 \
						--nodegroup-name standard-workers \
						--node-type t2.small \
						--nodes 2 \
						--nodes-min 1 \
						--nodes-max 3 \
						--node-ami auto \
						--region us-east-2 \
						--zones us-east-2a \
						--zones us-east-2b \
						--zones us-east-2c \
					'''
				}
			}
		}

		

		stage('Create conf file cluster') {
			steps {
				withAWS(region:'us-east-2', credentials: 'aws-static') {
					sh '''
						aws eks --region us-east-2 update-kubeconfig --name capstone.cluster
					'''
				}
			}
		}

	}
}
