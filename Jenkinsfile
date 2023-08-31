pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
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
         stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh' 
            }
        }
        stage('Manual Approval') {
            steps {
                input message: 'Lanjutkan ke tahap Deploy? (Klik "Proceed" untuk melanjutkan eksekusi pipeline ke Tahapan Deploy)' 
            }
        }
         stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                sleep time: 60, unit:'SECONDS'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
