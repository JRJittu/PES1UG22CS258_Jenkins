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
                build 'PES1UG22CS258-1'
                sh 'g++ ./main/hello.cpp -o outputt' // Error: Incorrect output file name
            }
         }

         stage('Test') {
            steps {
                sh './output' // Error: The file was compiled as 'outputt', so this will fail
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
            echo 'Pipeline failed' // Fixed incorrect use of 'error'
        }
    }
}
