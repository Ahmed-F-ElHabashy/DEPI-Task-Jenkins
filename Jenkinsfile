pipeline {
    agent any

    environment {
        COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Check Mongo and Mongo Express') {
            steps {
                script {
                    def mongoRunning = sh(script: 'docker ps --filter "name=mongo" --format "{{.Names}}"', returnStdout: true).trim()
                    def mongoExpressRunning = sh(script: 'docker ps --filter "name=mongo-express" --format "{{.Names}}"', returnStdout: true).trim()

                    if (mongoRunning) {
                        echo "Mongo is already running"
                    } else {
                        echo "No Mongo instance running"
                    }

                    if (mongoExpressRunning) {
                        echo "Mongo Express is already running"
                    } else {
                        echo "No Mongo Express instance running"
                    }

                    if (!mongoRunning && !mongoExpressRunning) {
                        sh 'docker-compose up -d'
                    } else if (mongoExpressRunning) {
                        echo "Mongo Express already exists"
                    } else {
                        sh 'docker-compose up -d mongo'
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
    }
}

