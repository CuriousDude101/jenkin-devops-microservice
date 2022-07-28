//SCRIPTED PIPELINE

//DECLARATIVE
pipeline {
	agent any
	stages{
		stage('Build') {
			steps {
				echo "Build"
			}

		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}

		}
	} 
	
	post {
		always {
			echo "I'm awesome. I run ALWAYS"
		}
		success {
			echo "I run when you are SUCCESSFUL"
		}
		failure {
			echo "I run when you FAIL"
		}
	}
}
