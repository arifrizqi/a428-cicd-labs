pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                checkout scm
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
                checkout scm
                sh './jenkins/scripts/test.sh' 
            }
        }
    }
}