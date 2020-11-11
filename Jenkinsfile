pipeline {
    agent any
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