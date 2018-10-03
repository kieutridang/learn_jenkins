pipeline {
  agent {
    docker {
      image 'node:10.11.0'
    }

  }
  stages {
    stage('Notify') {
      steps {
        echo 'New pull request'
        slackSend(message: 'there is a new pull request', baseUrl: 'https://avengers-freelancer.slack.com/services/hooks/jenkins-ci/', token: 'Pidi8OGP4Axa8UhqLAPIUFNI')
      }
    }
    stage('Prepare environment') {
      steps {
        sh '''
          npm --version
          node --version
          yarn install --network-timeout 1000000
        '''
      }
    }
    stage ('Code analyse') {
      steps {
        sh '''echo "Run some lints"'''
      }
    }
    stage ('Unit test') {
      steps {
        sh 'echo "Tests will back"'
      }
     
    }
    stage('Build') {
      environment {
        HOME = '.'
      }
      steps {
        sh '''
          npm run build
        '''
      }
    }
    stage('Final') {
      steps {
        echo 'build done'
      }
    }
  }
}
