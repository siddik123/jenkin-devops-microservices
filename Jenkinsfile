//Scripted pipeline Old Version
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Integration Test"
// 	}
// }

//Scripted pipeline New Version
// node {
// 	stage('Build')
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// 		echo "Deployed"
// }

//Declarative Piple line
pipeline {
	agent any  //agent is a image where your build will run
	//syntex how to use agen as a MAVEN docker with images
	//agent { docker { image 'maven:3.6.3'} } 
	//syntex how to use agen as a NODE docker with images
	//agent { docker { image 'node:15.11'} }
	stages {
		stage('Build') {
			steps {
				//for maven
				//sh 'mvn --version'
				//For node
				//sh 'node --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAMBE - $env.JOB_NAMBE"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
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