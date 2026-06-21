pipeline{
    agent any
    stages{
        stage('Deployment'){
            steps{
                sh """
                scp docker-compose.yaml ubuntu@13.234.213.25:/home/ubuntu/docker-compose.yaml
                ssh ubuntu@13.234.213.25 '''
                cd /home/ubuntu
                docker-compose down
                docker-compose up -d
                '''
                """
            }
        }
    }
}