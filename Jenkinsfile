pipeline {
	agent any
	stages {

		stage('Create kubernetes cluster') {
			steps {
				withAWS(region:'us-west-1', credentials: 'project05-udacity') {
					sh '''
						eksctl create cluster \
						--name capstonecluster \
						--version 1.13 \
						--nodegroup-name standard-workers \
						--node-type t2.small \
						--nodes 2 \
						--nodes-min 1 \
						--nodes-max 3 \
						--node-ami auto \
						--region us-west-1 \
						--zones us-west-1a \
						--zones us-west-1b \
						--zones us-west-1c \
					'''
				}
			}
		}

		

		stage('Create conf file cluster') {
			steps {
				withAWS(region:'us-west-1', credentials: 'project05-udacity') {
					sh '''
						aws eks --region us-west-1 update-kubeconfig --name capstonecluster
					'''
				}
			}
		}

	}
}
