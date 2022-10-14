//SCRIPTED

//DECLARATIVE
pipeline
{
	
	//agent any
	//agent { docker { image 'maven:3.6.3'} }
	agent { docker { image 'python:3.9.7'} }

	stages
	{
		stage('Build')
		{
			steps
			{
				//sh 'mvn --version'
				sh 'python --version'
				
		
				echo "Build"

			}

		}
		stage('Test')
		{
			steps
			{
				echo "Test"

			}

		}
		stage('Integration Test')
		{
			steps
			{
				echo " Integration Test"							   
			}

		}
	}

		
}




