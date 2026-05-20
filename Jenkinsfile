pipeline {
    agent {
        docker {
            image 'node:18-alpine'
        }
    }

    stages {
        stage('Load Dependencies') {
            steps {
                sh '''
                    npm --version
                    npm install @salesforce/cli --global
                    sf --version
                '''
            }
        }
    }
}