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
                echo "1. Execute container content in Kubernetes pod" 
                sh 'npm install'
            }
        }
        stage('Test') {
             
            steps {
                echo "2. Execute container content in Kubernetes pod" 
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
                  
            steps {
                echo "3. dExecute container content in Kubernetes pod"  
                echo currentBuild.result
                //xsh './jenkins/scripts/deliver.sh'
                //input message: 'Finished using the web site? (Click "Proceed" to continue)'
                //xsh './jenkins/scripts/kill.sh'
            }
        }
    }
}