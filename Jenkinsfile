/* Basic pipeline for multi-branch refer : https://www.youtube.com/watch?v=7KCS70sCoK0 */

CODE_CHANGE = getGitChanges() // it for check any code changes in git
BRANCH_NAME = 'BRANCH_NAME_VERIABLE'
pipeline {
	agent any
	stages{
		stage("docker-build"){
			when{ // custom condition
				expression{
					BRANCH_NAME=='master' || BRANCH_NAME=='dev' &&  CODE_CHANGE = true // condition with OR (||), match then it steps can executed else not.
				}
			}
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
	post{	
	/* used to execute after all step done */
		always{
			//run always failed or sucess
		}
		success{
			//run always sucess
		}
		failure{
			//run always failure
		}
	}
}
