pipeline {
    agent any


    stages {
        stage('Build Frontend') {
            steps {
                sh 'echo Build Front End'
                sh 'cd frontend_test && npm install && npm run build'
            }
        }
        
        stage('Deploy Frontend') {
            steps {
                sh "echo Deploying Frontend"
                script{
                    withAWS(region: 'us-east-1', credentials: 'AWS_CREDENTIALS'){
                        sh "aws s3 sync frontend/dist s3://bjgomes-bucket-sdet" 
                    }  
                }
            }
        }

        stage('Build Backend') {
            steps {
                sh "echo Building Backend"
                sh "cd jenkins-demo && mvn clean install"
            }
        }


    }

}
