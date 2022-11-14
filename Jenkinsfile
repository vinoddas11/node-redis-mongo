pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=Docker
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git  'https://github.com/vinoddas11/node-redis-mongo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t ahildarshan/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {

			steps {
				sh 'docker push ahildarshan/node:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
