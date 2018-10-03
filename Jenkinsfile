pipeline {
  agent {
    docker {
      image 'node:10:11.0'
    }

  }
  stages {
    stage('Notify') {
      steps {
        echo 'New pull request'
        slackSend(message: 'there is a new pull request', baseUrl: 'https://avengers-freelancer.slack.com/services/hooks/jenkins-ci/', token: 'Pidi8OGP4Axa8UhqLAPIUFNI')
      }
    }
    stage('Build') {
      environment {
        HOME = '.'
      }
      steps {
        sh '''npm --version
pwd
ls
yarn cache clear
yarn --network-timeout=999999
echo "code to build here"
'''
      }
    }
    stage('Stage 3') {
      steps {
        echo 'build done'
      }
    }
  }
}
