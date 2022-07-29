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
				sh "mvn clean compile"
			}

		}

		stage('Test') {
			steps {
				sh "mvn test"
			}
		}

		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}

		}

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}

		}

		stage('Build Docker Image'){
			steps{
				//"docker build -t manzzy/currency-exchange-devops:$env.BUILD_TAG"
				script{
					dockerImage = docker.build("manzzy/currency-exchange-devops:${env.BUILD_TAG}")
				}

			}

		}

		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('', 'dockerhub'){
						dockerImage.push();
						dockerImage.push('Latest');
					}

				}
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
