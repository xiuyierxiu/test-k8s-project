pipeline {
  agent any
  stages {
    stage('Pull code by web ui') {
      parallel {
        stage('Pull code by web') {
          steps {
            sh 'echo "pull code by web ui"'
          }
        }

        stage('Pull code by trigger') {
          steps {
            sh 'echo "pull code by trigger"'
          }
        }

      }
    }

    stage('Building and Scan') {
      parallel {
        stage('Building and Scan') {
          steps {
            container(name: 'build', shell: 'echo  "build"')
          }
        }

        stage('Scan code') {
          steps {
            container(name: 'test', shell: 'echo "test"')
          }
        }

      }
    }

    stage('Build Image') {
      steps {
        container(name: 'docker', shell: 'echo "build image"')
      }
    }

    stage('Deploy') {
      steps {
        container(name: 'deploy', shell: 'echo "Deploy to k8s"')
      }
    }

  }
}