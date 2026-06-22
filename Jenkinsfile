pipeline {
    agent any

    stages {
        stage('Deployment') {
            steps {
                sh """
                scp docker-compose.yaml ubuntu@3.108.223.48:/home/ubuntu/docker-compose.yaml

                ssh ubuntu@3.108.223.48 '
                cd /home/ubuntu
                docker compose down
                docker compose up -d
                '
                """
            }
        }
    }
}