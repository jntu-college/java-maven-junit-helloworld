#!/groovy


pipeline{
	agent any
	stages{
		stage('Clean'){
			echo "Deleting workspace"
			deleteDir()
		}

		stage('Checkout'){
			checkout scm
		}

		stage('Compile'){
			script{
				sh 'mvn clean compile'
			}

		}

		stage('Testing'){
			script{
				sh 'mvn test'
			}

		}

		stage('Build'){
			script{
				sh 'mvn package'
			}

		}
	}
}
