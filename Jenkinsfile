//SCRIPTED

//DECLARATIVE
pipeline
{
	
	//agent any
	agent { docker { image 'maven:3.8.6'} }

	stages
	{
		stage('Build')
		{
			steps
			{
				sh 'mvn --version'
				sh 'node --version'
				echo "Build Test"

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




