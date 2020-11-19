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
        kubernetes {
            defaultContainer 'jnlp'
            yamlFile 'jenkins/mainPod.yaml'
        }

    }
    
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
                  
            steps {
                container('nodejs') { 
                    echo "1. Execute container content in Kubernetes pod" 
                    sh 'mkdir /root/.ssh && chmod 0700 /root/.ssh'
                    sh 'ssh-keyscan -t rsa github.wdf.sap.corp >> ~/.ssh/known_hosts'
                    git url: 'git@github.wdf.sap.corp:sf-workzone-for-hr/sf-workzone-contentpackage.git', branch: 'master'
                    sh 'cd sf-workzone-contentpackage'
                    sh 'ls -al'
                    //sh 'npm install'
                }
            }
        }
        stage('Test') {
             
            steps {
                container('sapjvm8') {
                    echo "2. Execute container content in Kubernetes pod" 
                    sh 'java -version'
                     //sh './jenkins/scripts/test.sh'
                }
            }
        }
        stage('Deliver') {
                  
            steps {
                container('sapjvm8') {
                    echo "3. dExecute container content in Kubernetes pod"  
                    echo currentBuild.result
                    //xsh './jenkins/scripts/deliver.sh'
                    //input message: 'Finished using the web site? (Click "Proceed" to continue)'
                    //xsh './jenkins/scripts/kill.sh'
                }
            }
        }
    }
}