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
                    npm config set prefix ~/.local 
                    ls -la
                    # npm install @salesforce/cli --global
                    # sf --version
                '''
            }
        }
    }
}