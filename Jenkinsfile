pipeline{
	agent any

	stages{
		stage('Build'){
			steps{
				sh 'mvn -f /deploy/Udemy/maven-project/pom.xml clean package'
			}
			post{
				success{
				echo 'Now Archive]ing...'
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