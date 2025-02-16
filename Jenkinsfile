node {
    stage('Build') {
        echo 'Building the project...'
        try {
            docker.image('node:16-buster-slim').inside("-p 3000:3000") {
                sh 'npm install'
            }
        } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Build failed: ${e.message}"
        }
    }
    stage('Test') {
        echo 'Running tests...'
        try {
            docker.image('node:16-buster-slim').inside("-p 3000:3000") {
                sh './jenkins/scripts/test.sh'
            }
        } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Tests failed: ${e.message}"
        }
    }
   
}