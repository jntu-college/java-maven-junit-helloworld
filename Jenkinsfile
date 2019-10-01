#!/groovy

def branch

pipeline{
	agent any
	stages{
		stage('Clean'){
			steps{
				echo "Deleting workspace"
				deleteDir()
			}
			
		}

		stage('Checkout'){
			steps{
				checkout scm
				script{
					branch = env.BRANCH_NAME
					echo "The current branch is ${branch}"
				}
				
			}
			
		}

		stage('Compile'){
			steps{
				script{
				sh 'mvn clean compile'

				}
			}
			

		}

		stage('Testing'){
			steps{
				script{
				sh 'mvn test'
				}
			}
		}

		stage('Build'){
			steps{
				script{
					sh 'mvn package'
				}
			}
		}

		stage('Dev Code Deployment'){
			when {
				expression { branch == 'dev'}
			}
			steps{
				script{
					echo "Development code is deploying"
				}
			}
		}

		stage('Master Code Deployment'){
			when {
				expression { branch == 'master'}
			}
			steps{
				script{
					echo "Production code is deploying"
				}
			}
		}
	}
}
