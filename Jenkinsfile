pipeline {
    agent any
    stages {
        stage('Prune Docker data') {
            steps {
                echo 'docker image prune -a -f'
            }
        }
    }
    post {
        always {
            sh 'docker compose ps'
        }
    }
}
