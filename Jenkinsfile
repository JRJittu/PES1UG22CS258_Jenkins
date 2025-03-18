pipeline {
    agent any
    stages {
         stage('Clone repository') {
             steps {
                 checkout([$class: 'GitSCM',
                 branches: [[name: '*/main']],
                 userRemoteConfigs: [[url: 'https://github.com/JRJittu/PES1UG22CS258_Jenkins.git']]])
             }
         }

         stage('Build') {
            steps {
                build 'PES1UG22AM191-1'
                sh 'g++ ./main/hello.cpp -o output'
            }
         }

         stage('Test') {
            steps {
                sh './output'
            }
         }

         stage('Deploy') {
            steps {
                echo 'deploy'
            }
         }
    }
   
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
