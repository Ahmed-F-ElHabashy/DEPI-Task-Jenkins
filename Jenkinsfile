pipeline {
    agent any

    environment {
        COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Checking Mongo and Mongo Express') {
            steps {
                script {
                    def mongoExpressRunning = sh(script: 'docker ps --filter "name=mongo-express" --format "{{.Names}}"', returnStdout: true).trim()

                    if (mongoExpressRunning) {
                        echo "Mongo Express is already running"
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

