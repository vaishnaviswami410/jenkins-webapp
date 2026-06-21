pipeline {
    agent any

    stages {
        stage('Deployment') {
            steps {
                sh """
                scp docker-compose.yaml ubuntu@13.201.13.88:/home/ubuntu/docker-compose.yaml

                ssh ubuntu@13.201.13.88 '
                cd /home/ubuntu
                docker compose down
                docker compose up -d
                '
                """
            }
        }
    }
}