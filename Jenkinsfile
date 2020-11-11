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
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}