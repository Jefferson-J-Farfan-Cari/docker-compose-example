pipeline {
    agent any
    stages {
        stage("verify tooling") {
            steps {
                sh '''
                docker version
                docker info
                docker compose version 
                curl --version
                '''
            }
        }
        stage('Prune Docker data') {
            steps {
                sh 'docker volume prune'
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
    post {
        always {
            sh 'docker compose down'
            sh 'docker compose ps'
        }
    }
}
