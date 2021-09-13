pipeline {
    // master executor should be set to 0
    agent any
    stages {
		stage('Pull Latest Image') {
            steps {
                //sh
                bat "docker pull iamprotyoy/selenium-docker"
            }
        }
        stage('Start Grid') {
            steps {
                //sh
                bat "docker-compose up -d hub chrome firefox"
            }
        }
		stage('Run Test') {
            steps {
                //sh
                bat "docker-compose up search-module book-flight-module"
            }
        }
    }
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			//sh
            bat "docker-compose down"
		}
	}
}