pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('admin')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git  'https://github.com/Darshants16081995/node-redis-mongo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t darshants/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {

			steps {
				sh 'docker push darshants/node:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
