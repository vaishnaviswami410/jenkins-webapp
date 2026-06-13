pipeline{
    agent any
    environment{
        IMAGE_NAME= "vaishnaviswami410/frontend-app"
        IMAGE_TAG= "${BUILD_NUMBER}"
        APP_SERVER= "15.207.16.72"
        }
        stages {
            stage('checkout'){
             steps{
               git branch: 'main',
               url: 'https://github.com/vaishnaviswami410/jenkins-webapp.git'
        }
        
            }
             
        stage('Docker Login'){
            steps{
                withCredentials([
                    usernamePassword(
                        credentialsID: 'DockerCred',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {
                    sh '''
                    echo $DOCKER_PASS | docker login \
                    -u $DOCKER_USER \
                    --password-stdin
                    '''
                }
                      
            }
        }
        stage('push Image'){
            steps{
                sh '''
                docker push $IMAGE_NAME:$IMAGE_TAG
                docker tag\
                $IMAGE_NAME:$IMAGE_TAG\
                $IMAGE_NAME:latest
                docker push $Image_NAME:latest
                '''
            }
        }
        stage('Deploy to App Server') {
            steps {
                sh """
                ssh ubuntu@$APP_SERVER '
                docker pull $IMAGE_NAME:latest
                docker stop frontend || true 
                docker run -d \
                --name frontend \
                -p 80:80
                $IMAGE_NAME:latest
                '
                """
            }
        }
    }
    Post {
        Success {
            echo "Delployment Successful!"
        }
       failure{
        echo "Deployment Failed"
    }
}
}
