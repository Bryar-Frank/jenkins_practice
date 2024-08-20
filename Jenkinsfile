pipeline {
    agent any

    stages{
        stage('Build Frontend'){
            steps{
                sh "echo Building frontend"
                sh "cd frontend_test && npm install && npm run build"
                
            }
        
            }
        stage('Deploy Frontend'){
            steps{
                script{
                    try {
                      withAWS(region: 'us-east-1', credentials: 'AWS_CREDENTIALS'){
                        sh "aws s3 sync frontend_test/dist s3://bjgomes-bucket-sdet" 
                        }catch (Exception e) {
                            echo "${e}"
                            throw e
                        }   
                    }
                }
            }
        }
        stage('Build Backend'){
            steps{
                sh "cd jankins-demo && mvn clean install"
            }
        }
        stage('Test Backend'){
            steps{
                sh "cd jenkins-demo && mvn test"
            }
        }
        stage('Deploy Backend'){
            steps{
                try {
                      withAWS(region: 'us-east-1', credentials: 'AWS_CREDENTIALS'){
                        sh "aws s3 sync demo/target/*.jar s3://bjgomes-bucket-sdet-backend" 
                        }catch (Exception e) {
                            echo "${e}"
                            throw e
                        }   
                    }
            }
        }
    }
}
