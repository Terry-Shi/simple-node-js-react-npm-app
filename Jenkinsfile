// pipeline {
//     agent any
//     stages {
//         stage('UT') { 
//             steps {
//                 sh 'ls -al' 
//             }
//         }
//         stage('Build') { 
//             steps {
//                 sh 'npm install' 
//             }
//         }
//         stage('Deploy') { 
//             steps {
//                 sh 'ls -al' 
//             }
//         }
//     }
// }
pipeline {
    agent {
        docker {
            image 'node:15-alpine' 
            args '-p 3000:3000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}