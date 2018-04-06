pipeline{
	agent { label 'slave1' }

	stages{
		stage('Build'){
			steps{
				sh 'mvn clean package'
			}
			post{
				success{
				echo 'Now Archive]ing...'
				sh 'ls -ltr'
				archiveArtifacts artifacts: '**/target/*.war'
				}
			}
		}

		stage('Deploy to Staging'){
			steps{
				build job: 'Udemy/deploy-to-staging'
			}
		}
	}
}