#!/usr/bin/env groovy

pipeline {
   agent any
  //agent { label 'executor-v2' }

//   options {
//     ansiColor('xterm')
//     timestamps()
//     buildDiscarder(logRotator(daysToKeepStr: '30'))
//   }

//   triggers {
//     cron(getDailyCronString())
//   }

  stages {
    stage("clone"){
      steps{
        echo "git clone"
      }
    }
    stage('conjur secret') {
      steps {
        withCredentials([conjurSecretCredential(credentialsId: 'host1apikey_password_fromjenkinsfile', variable: 'CONJUR_SECRET')]) {
            sh 'echo $CONJUR_SECRET | base64'    
        }
      }
    }
  }
}
