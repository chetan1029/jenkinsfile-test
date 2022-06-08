node {

    def candi_frontend
    def candi_backend
    def candi_parser

    stage('Checkout') {
        checkout scm
    }
    stage('Build') {
        candi_frontend = docker.build("armdocker.rnd.ericsson.se/stsi/ddcandi-frontend:0.0.1", "./frontend")
        candi_backend = docker.build("armdocker.rnd.ericsson.se/stsi/ddcandi-backend:0.0.1", "./backend") 
        candi_parser = docker.build("armdocker.rnd.ericsson.se/stsi/ddcandi-parser:0.0.1", "./parser-api") 
    }
    stage('Test') { 
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
    stage('Deploy') {
        // candi_frontend.push()
        // candi_backend.push()
        // candi_parser.push() 
    }
}