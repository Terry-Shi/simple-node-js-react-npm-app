pipeline {
    // agent {
    //     docker {
    //         image 'node:6-alpine' 
    //         args '-p 3000:3000' 
    //     }
    // }
    stages {
        stage('UT') { 
            steps {
                sh 'ls -al' 
            }
        }
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Deploy') { 
            steps {
                sh 'ls -al' 
            }
        }
    }
}