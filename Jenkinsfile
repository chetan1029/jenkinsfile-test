pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                def candi_frontend = docker.build("armdocker.rnd.ericsson.se/stsi/ddcandi-frontend:0.0.1", "./frontend")
                def candi_backend = docker.build("armdocker.rnd.ericsson.se/stsi/candi-backend:0.0.1", "./backend") 
                def candi_parser = docker.build("armdocker.rnd.ericsson.se/stsi/candi-parser:0.0.1", "./parser-api") 
            }
        }
        stage('Test') { 
            steps {
                candi_frontend.inside {
                    sh 'node --version'
                }
                candi_backend.inside {
                    sh 'node --version'
                }
                candi_parser.inside {
                    sh 'python --version'
                }
            }
        }
    }
    // stage('Artifactory') {
    //     candi_frontend.push()
    //     candi_backend.push()
    //     candi_parser.push() 
    // }
}