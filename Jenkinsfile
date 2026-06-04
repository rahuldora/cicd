pipeline {
    agent any

    environment {
        HUB_ORG="dora.rahul0007.196b04ad0501@agentforce.com"
        SFDC_HOST="https://login.salesforce.com"
        CONSUMER_KEY=credentials('consumer_key')
        JWT_CRED_ID=credentials('server_key')
    }

    stages {

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Authenticate SFDX') {
            agent {
                docker {
                    image 'rahuldora/sfcli-alpine:latest'
                }
            }
            steps {
                sh '''
                    sf -v
                    #sf org login jwt --username $HUB_ORG --jwt-key-file $JWT_CRED_ID --client-id $CONSUMER_KEY
                '''

            }
        }
    }
}
