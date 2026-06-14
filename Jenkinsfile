pipeline {
    agent any

    environment {
        STACK_NAME = "voting-stack"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/RashwinPonnanna/example-voting-app.git'
            }
        }

        stage('Build Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy to Swarm') {
            steps {
                sh 'docker stack deploy -c docker-stack.yml ${STACK_NAME}'
            }
        }
    }

    post {
        success {
            echo 'Deployed to Docker Swarm successfully!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}
