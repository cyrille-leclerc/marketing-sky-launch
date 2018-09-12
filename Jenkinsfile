pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        withMaven() {
          sh 'mvn clean package'
        }
        
      }
    }
    stage('Parallel Stage') {
      failFast true
      parallel {
        stage('Code Static Analysis') {
          steps {
            echo 'analyze...'
          }
        }
        stage('Web Browser Tests') {
          steps {
            echo 'test...'
            sh 'echo \'hello\''
          }
        }
        stage('') {
          steps {
            sleep 5
          }
        }
      }
    }
  }
  triggers {
    eventTrigger simpleMatch('maven://com.example:my-framework')
  }
}
