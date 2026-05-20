pipeline {
    agent {
        docker {
            image 'salesforce/cli:latest-slim'
        }
    }

    stages {
        stage('Create Deployment Package') {
            steps {
                sh '''
                    ls -la
                '''
            }
        }
    }
}