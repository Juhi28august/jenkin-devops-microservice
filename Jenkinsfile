//SCRIPTED

//DECLARATIVE
pipeline
{
	
	agent any
	//agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'python:3.9.7'} }

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	} 
	stages
	{
		stage('Checkout')
		{
			steps
			{
				sh 'mvn --version'
				sh 'docker version'
				//sh 'python --version'
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
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test')
		{
			steps
			{
				sh "mvn Test"

			}

		}
		stage('Integration Test')
		{
			steps
			{
				sh "mvn failsafe:integration-test failsafe:varify"							   
			}
		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}	

		}
		stage ('Build Docker Image') {
			steps{
				//"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("rajan0770/currency-exchange-devops:${env.BUILD_TAG}")
				}

			}
		}

		stage ('push Docker Image') {
			steps{
				script{
					docker.withRegistry('','dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
					
				}
				
			}
		}
	 
	

		
}




