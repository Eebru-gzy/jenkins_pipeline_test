pipeline {
  agent any
  stages {
    stage('One') {
      steps {
        echo 'Hi, Eebru testings first pipeline'
      }
    }
    stage('Two') {
      steps {
        input('Hey eebru, do you want to proceed?')
      }
    }
    stage('Three') {
      when {
        not {
          branch 'master' 
        }
        steps {
          echo 'Not master branch'
        }
      }
    }
    stage('Four') {
      parallel {
        stage('unit test') {
          steps {
            echo 'Running Unit test' 
          }
        }
        stage ('Integration test') {
          agent {
            docker {
              reuseNode false
              image 'ubuntu'
            }
          }
          steps {
            echo 'running integration tests'
          }
        }
      }
    }
  }
}
