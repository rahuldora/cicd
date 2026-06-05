pipeline {
    agent any

    environment {
        HUB_ORG = credentials('devhub_username')
        CONSUMER_KEY = credentials('consumer_key')
    }

    stages {

        stage('Checkout SCM') {
            steps {
                checkout scmGit(
                    branches: [[name: '*']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/rahuldora/cicd.git'
                    ]]
                )
            }
        }

        stage('Authenticate SFDX') {

            agent {
                docker {
                    image 'rahuldora/sfcli-alpine:latest'
                    args '-u root'
                }
            }

            environment {
                HOME = "/tmp"
            }

            steps {

                withCredentials([
                    file(credentialsId: 'server_key', variable: 'JWT_KEY_FILE')
                ]) {

                    sh '''
                        sf org login jwt \
                          --username $HUB_ORG \
                          --jwt-key-file $JWT_KEY_FILE \
                          --client-id $CONSUMER_KEY
                    '''
                }
            }
        }
    }
}
