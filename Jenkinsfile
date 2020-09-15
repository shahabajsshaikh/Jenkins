/* Basic pipeline */

pipeline {
	agent any
	stages{
		stage("docker-build"){
			steps{
				echo 'git clone'
				/*git credentialsId: 'github', url: 'https://github.com/shahabajsshaikh/Jenkins.git'*/
			}
		}
		stage("docker-push"){
			steps{
				echo 'docker build started...'
				/*sh 'docker info'
				sh 'docker build -t .'
				sh 'docker push'*/
			}
		}
	}
}
