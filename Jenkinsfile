pipeline {
    agent any
    tools {
        nodejs 'NodeJS' // Use the name you configured in the Global Tool Configuration
    }
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
