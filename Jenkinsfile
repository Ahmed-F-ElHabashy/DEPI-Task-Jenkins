pipeline {
    agent any

    stages {
        stage('Welcome Message') {
            steps {
                echo "Hello $loggedusername .. Hope you are doing well ISA .."
            }
        }
        stage('Checking the Docker Process Status ..') {
            steps {
                sh 'docker ps'
                sh 'docker compose ps'
            }
        }
         stage('Starting the YML file Container ...') {
            steps {
                sh 'docker compose up -d'
                sh 'docker compose ps'
            }
            post {
                failure {
                sh 'docker compose down --remove-orphans -v'
                sh 'docker compose ps'
                sh 'docker compose up -d' 
                }
                success {
                    echo"Done .. its Running Successfully now .. Have Fun Habashyyyy.."
                }

                

            }
        }
    }
    
}
