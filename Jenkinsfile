pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 7000:7000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
    }
}