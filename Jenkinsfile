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
	stages{
		stage('Build'){
			steps{
					echo "Build"
			}
		}
		stage('Test'){
			steps{
					echo "Test"
			}
		}
		stage('Integration Test'){
			steps{
					echo "Integration Test"
			}
		}
		stage('Deploy'){
			steps{
					echo "Deploy"
			}
		}
	}
	post{
		always{
			echo 'i am awsome always RUN'
		}
		success{
			echo 'i am run when build successfull'
		}
		failure{
			echo 'i am run when Build Failed'
		}
	}
}