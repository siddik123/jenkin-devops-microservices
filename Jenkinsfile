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
		//Build Jar
		stage('Package') {
			steps {
					sh "mvn package -DskipTests"
			}
		}

		stage('Deploy') {
			steps {
					echo "Deploy"
			}
		}
		stage('Build Docker Image') {
			steps {
				//"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
				script {
					//docker.build("in28min/currency-exchange-devops:$env.BUILD_TAG")
					//or
					dockerImage = docker.build("m123mmahad/hello-world-java:${env.BUILD_TAG}")
				}	
			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					//Docker Hub credential
					docker.withRegistry('', 'aa8611c6-f269-48ef-b12a-e6e6803cc0d9'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}					
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

