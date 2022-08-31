pipeline {
    agent any
    stages {
        stage('Prune Docker data') {
            steps {
                bat 'docker image prune -a -f'
            }
        }
        stage('Start container') {
            steps {
                bat 'docker-compose up -d --build'
                bat 'docker compose ps'
            }
        }
        stage('Run tests against the container') {
            steps {
                bat 'curl http://localhost:3000/param?query=demo'
            }
        }
    }
    post {
        always {
            bat 'docker compose ps'
        }
    }
}
