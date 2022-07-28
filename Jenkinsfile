//SCRIPTED PIPELINE

//DECLARATIVE
pipeline {
	agent any
	// agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'node:18.7.0'} }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages{
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "JOB NAME - $env.JON_NAME"
				echo "BUILD TAG - $env.BUILD_TAG"
				echo "BUILD URL - $env.BUILD_URL"

			}

		
		}
		stage('Compile'){
			steps{
				sh "mv clean compile"
			}

		}

		stage('Test') {
			steps {
				echo "mvn Test"
			}
		}

		stage('Integration Test') {
			steps {
				echo "mvn failsafe:integration-test failsafe:verify"
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
