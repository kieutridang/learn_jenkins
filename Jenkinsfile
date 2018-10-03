pipeline {
  agent {
    docker {
      image 'node:latest'
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
