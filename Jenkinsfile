pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 4000:4000' 
        }
    }
    stages {
        stage('Preparation') {
            steps {
                sh 'npm cache clean --force'
            }
        }
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
    }
}