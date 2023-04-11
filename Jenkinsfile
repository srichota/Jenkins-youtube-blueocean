pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''pwd
date'''
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'test step'
          }
        }

        stage('test part') {
          steps {
            echo 'test part'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        echo 'deploy'
        sleep 10
      }
    }

  }
}