pipeline {
    agent any
    stages {
        stage('Prune Docker data') {
            steps {
                sh 'docker image prune -a -f'
            }
        }
        stage('Start container') {
            steps {
                sh 'docker-compose up -d --build'
                sh 'docker compose ps'
            }
        }
        stage('Run tests against the container') {
            steps {
                sh 'curl http://localhost:3000/param?query=demo'
            }
        }
    }
}
