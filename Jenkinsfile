/* Basic pipeline for multi-branch refer : https://www.youtube.com/watch?v=7KCS70sCoK0 */


// ENV Veriable: you can get all details via ====> http://<public-ip>:8080/env-vars.html/

pipeline {
	 environment {
		 registry = "shahabajsshaikh/test"  
	 }
	agent any
	stages{
		stage("Git-clone"){
			agent any
			steps{
				echo '********************************Stage-1********************************'
				git credentialsId: 'github', url: 'https://github.com/shahabajsshaikh/Jenkins.git'
				sh 'ls && pwd'
				echo '********************************Git-clone completed..!********************************'	
			}
		}
		stage("Conatiner"){
			agent any
			steps{
				 buildApp()
			}
			
		}
		stage("Build"){
			agent any
			steps{
				echo 'Build start'
				echo 'Build done sucessfully'	
			}
		}
		stage("docker-build"){
			agent any
			steps{
				echo 'build in process'	
				script { 
					dockerImage = docker.build registry + ":$BUILD_NUMBER" 
				}
				echo ("$dockerImage")
				// docker.build registry + 
				//dockerImage = docker.build registry + ":$BUILD_NUMBER"		
			}
		}
		stage("docker-push"){
			agent any
			steps{
				echo 'docker pushing started...'
				sh 'pwd && ls'
				sh 'docker images'
				script { 	
					withDockerRegistry(credentialsId: 'docker', url: 'https://index.docker.io/v1/'){
						echo "Login successfully..!" //  https://registry.hub.docker.com/
						script {
							echo ("before")
							dockerImage.push("$BUILD_NUMBER")
							echo ("after")
						}
						
						sleep time: 5, unit: 'MICROSECONDS'
					}
					echo "Pushed successfully..!"
					sh 'docker rmi -f $(docker images -a -q)'
					echo "Remove images successfully..!"
				}
			}
		}
	}
}

def buildApp() {
	script { 
		docker.image('httpd').inside { sh 'ls'}
		//withDockerContainer("shahabajsshaikh/openjdk8:0.0"){
			
			//sh 'ls && pwd'
		//}
	}

	
	/* node('dockers'){
		def maven = docker.image('shahabajsshaikh/openjdk8:0.0')
		maven.pull()
		maven.inside {
			sh 'ls'
		}
	}*/
}
