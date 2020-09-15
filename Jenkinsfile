/* Basic pipeline for multi-branch refer : https://www.youtube.com/watch?v=7KCS70sCoK0 */


// ENV Veriable: you can get all details via ====> http://<public-ip>:8080/env-vars.html/

pipeline {
	agent any
	stages{
		stage("docker-login"){
			agent any
			steps{
				echo 'git login'
				git credentialsId: 'github', url: 'https://github.com/shahabajsshaikh/Jenkins.git'
				
				echo 'docker login'
				withDockerRegistry(credentialsId: 'docker', url: 'https://index.docker.io/v1/'){ //https://registry.hub.docker.com/
    				// some block
				echo "login successfully..!"
				}	
			}
		}
		stage("docker-build"){
			agent any
			steps{
				echo 'build in process'
				sh 'docker build -t shahabajsshaikh/test:0.1 .'			
			}
		}
		stage("docker-push"){
			agent any
			steps{
				echo 'docker pushing started...'
		
				sh 'pwd && ls'
				sh 'docker images'
				
				withDockerRegistry(credentialsId: 'docker', url: 'https://registry.hub.docker.com/'){
					
					bat 'docker push shahabajsshaikh/test:0.1'
    				// some block
					echo "login successfully..!"
				}
				/*sh 'docker build -t .'
				sh 'docker push'*/
			}
		}
	}
}
