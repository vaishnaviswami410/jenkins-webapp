pipeline{
    agent any
    stages{
        stage('Deployment'){
            steps{
                sh """
                scp docker-compose.yaml ubuntu@35.154.193.204:/home/ubuntu/docker-compose.yaml
                ssh ubuntu@35.154.193.204 '''
                cd /home/ubuntu
                docker-compose down
                docker-compose up -d
                '''
                """
            }
        }
    }
}