pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout([
                        $class: 'GitSCM', 
                        branches: [[name: '*/master']], 
                        userRemoteConfigs: [[
                            url: 'https://github.com/AnuragP170/simple-node-js-react-npm-app',
                            credentialsId: 'github-pat'
                        ]]
                    ])
                }
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}


// pipeline {
//     agent any
//     stages {
//         stage('Build') { 
//             steps {
//                 sh 'npm install' 
//             }
//         }
//     }
// }
