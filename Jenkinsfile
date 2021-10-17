pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-vakhob')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t vakhob/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push vakhobdevops/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
