//SCRIPTED PIPELINE

//DECLARATIVE
pipeline {
	agent any
	// agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'node:18.7.0'} }

	stages{
		stage('Build') {
			steps {
				//sh 'mvn --version'
				//sh 'node --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "JOB NAME - $env.JON_NAME"
				echo "BUILD TAG - $env.BUILD_TAG"
				echo "BUILD URL - $env.BUILD_URL"

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
