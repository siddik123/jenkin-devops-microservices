//Declarative Piple line
pipeline {
	agent any 
	//agent { docker { image 'maven:3.6.3'} } 
	//agent { docker { image 'node:15.11'} }
	environment {
		/*Pointing To DockerHome where we install a docker in 
		a Global variable Configuration injenkins
		*/
		dockerHome = tool 'myDocker'
		/*Pointing To MavenrHome where we install a docker in 
		a Global variable Configuration injenkins
		*/
		mavenHome = tool 'myMaven'
		//Set the Maven and Docker path to the Bin folder
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				//Print maven Version
				sh 'mvn --version'
				//Print Docker Version
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps {
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
		stage('Deploy') {
			steps {
					echo "Deploy"
			}
		}
	}

	post {
		always {
			echo 'i am awsome always RUN'
		}
		success {
			echo 'i am run when build successfull'
		}
		failure {
			echo 'i am run when Build Failed'
		}
	}
}