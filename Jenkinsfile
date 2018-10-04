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
        slackSend(message: 'Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}', baseUrl: 'https://avengers-freelancer.slack.com/services/hooks/jenkins-ci/', token: 'Pidi8OGP4Axa8UhqLAPIUFNI')
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
    stage('Code analyse') {
      steps {
        sh 'echo "Run some lints"'
      }
    }
    stage('Unit test') {
      steps {
        sh 'echo "Tests will back"'
      }
    }
    stage('Build') {
      steps {
        sh '''
          npm run build
        '''
      }
    }
    stage('Deploy for master') {
      when {
        branch 'master'
      }
      steps {
        sh 'echo "This is master and will be deployed"'
      }
    }
    stage('Final') {
      steps {
        echo 'build done'
      }
    }
  }
}