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
				archiveArtifacts artifacts: '**/*.war'
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