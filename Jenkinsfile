pipeline{
    agent any
    stages{
        stage('Pre Build Actions'){
            steps{
               sh 'npm install'
                sh 'sudo systemctl status nginx || sudo apt install nginx -y'
                sh ' sudo systemctl start nginx'
            }
        }
        stage('Build'){
            steps{
                sh 'npm run Build'
            }
        }
        stage('Post Build Action'){
            steps{
                sh 'echo "Build Completed Successfully"'
                sh 'sudo cp -r dist/* /var/www.html/'
                sh 'sudo systemctl restart nginx'            
            }
        }
    }
}