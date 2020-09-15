# Basic pipeline:

pipeline {
	agent any
	stages{
		stage('docker-build')
		{
			step{
				echo 'git clone'
				git credentialsId: 'github', url: 'https://github.com/shahabajsshaikh/Jenkins.git'
			}
		}
		stage('docker-push')
		{
			step{
				echo 'docker build started...'
				sh 'docker info'
				sh 'docker build -t .'
				sh 'docker push'
			}
		}
	}
}
