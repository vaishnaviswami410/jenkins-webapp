pipeline {
    agent any

    stages {
        stage('Deployment') {
            steps {
                sh """
                scp docker-compose.yaml ubuntu@13.206.99.164:/home/ubuntu/docker-compose.yaml

                ssh ubuntu@13.206.99.164 '
                cd /home/ubuntu
                docker compose down
                docker compose up -d
                '
                """
            }
        }
    }
}