pipeline {
    agent any
    triggers {
        eventTrigger(event(generic('maven://com.example:my-framework')))
    }
    stages {
        stage ('Build') {
            steps {
                withMaven() {
                    sh "mvn clean package"
                }
            }
        }
        stage('Parallel Stage') {
            failFast true
            parallel {
                stage('Code Static Analysis') {
                    steps {
                        echo "analyze..."
                    }
                }
                stage('Web Browser Tests') {
                   steps {
                       echo "test..."
                   }
                }
            }
         }
    }
}