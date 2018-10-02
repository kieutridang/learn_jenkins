pipeline {
  agent any
  stages {
    stage('Stage 1') {
      steps {
        echo 'New pull request'
        slackSend(message: 'there is a new pull request', baseUrl: 'https://avengers-freelancer.slack.com/services/hooks/jenkins-ci/', token: 'Pidi8OGP4Axa8UhqLAPIUFNI')
      }
    }
    stage('Build') {
      steps {
        sh '''sh \'npm --version\'
sh \'npm run build\''''
      }
    }
    stage('Stage 3') {
      steps {
        echo 'build done'
      }
    }
  }
}