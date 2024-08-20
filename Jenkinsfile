pipeline {
    agent any


    stages {
        stage('Build') {
            steps {
                sh 'echo Building Stage 1'
            }
        }
        
        stage('Test') {
            steps {
                sh 'echo Testing Stage 2'
            }
        }
        
        stage('TestWebHook') {
            steps {
                sh 'echo Testing Web Hook'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'echo Deploying AWS'
            }
        }
    }

}
