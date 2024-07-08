pipeline {
    agent any

    stages {
        stage('Welcome Message') {
            steps {
                echo "Hello $loggedusername .. Hope you are doing well ISA .." //matensash t add it as string inside the Jenkins :D
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
                script {
                    // Start the containers
                    sh 'docker compose up -d'
                    sh 'docker compose ps'
                }
            }
            post {
                success {
                    echo "Done .. its Running Successfully now .. Have Fun Habashyyyy.."
                }
                failure {
                    // In case of failure, clean up and attempt to start again
                    script {
                        sh 'docker compose down --remove-orphans -v'
                        sh 'docker compose up -d'
                    }
                }
            }
        }
    }
}
