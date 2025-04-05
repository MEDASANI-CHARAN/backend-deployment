pipeline {
    agent {
        label 'agent-1'
    }
    options {
                // timeout(time: 100, unit: 'SECONDS')
                timeout(time: 5, unit: 'MINUTES')
                disableConcurrentBuilds() 
                 ansiColor('xterm')
            }
    parameters {
        string(name: 'appVersion', defaultValue: '1.0.0', description: 'What is the appication version?')

    }
    environment {
        def appVersion = '' //variable declaration
        nexusUrl = 'jenkins-nexus.daws78s.xyz:8081'
    }
    stages {
        stage('print the version') {
            steps {
                echo "Application version: ${params.appversion}"
            }
        }
        stage('Deploy') {
            steps {
                script {
                    build job: 'backend-deployment', parameters: [string(name: 'appVersion', value: 'stage')], propagate: false
              }
            }
        }
    }
        
    post { 
            always { 
                echo 'I will always say Hello again!'
                deleteDir()
            }
            success { 
                echo 'I will run when pipeline sucess'
            }
            failure { 
                echo 'I will run when pipeline failure'
            }
        }
    }
