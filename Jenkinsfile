#!/usr/bin/env groovy

pipeline{
    agent {label 'linux_agent_NTT'}
    stages{
        stage("cyberark conjur provided"){
            steps{
              withCredentials([conjurSecretCredential(credentialsId: 'db_password', variable: 'CONJUR_SECRET')]) {
                  sh 'echo $CONJUR_SECRET | base64'
                }
            }
        }
        stage("manual cred"){
            steps{
                withCredentials([conjurSecretCredential(credentialsId: 'password1', variable: 'CONJUR_SECRET_1')]) {
                    sh "echo $CONJUR_SECRET_1 | base64"
                }
            }
        }
    }
}
