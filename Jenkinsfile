node {

    def candi_frontend
    def candi_backend
    def candi_parser

    stage('Checkout') {
        checkout scm
    }
    stage('Build') {
        candi_frontend = docker.build("armdocker.rnd.ericsson.se/stsi/ddcandi-frontend:0.0.${env.BUILD_ID}", "./frontend")
        candi_backend = docker.build("armdocker.rnd.ericsson.se/stsi/ddcandi-backend:0.0.${env.BUILD_ID}", "./backend") 
        candi_parser = docker.build("armdocker.rnd.ericsson.se/stsi/ddcandi-parser:0.0.${env.BUILD_ID}", "./parser-api") 
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
    // stage('Deploy') {
    //     candi_frontend.push()
    //     candi_backend.push()
    //     candi_parser.push() 
    // }
    stage('Kubernetes Deploy') { 
        sh 'chmod +x ./k8s-deployment-candi-prod-test.yaml'
        sh "sed -i 's|BUILD_ID|${env.BUILD_ID}|' ./k8s-deployment-candi-prod-test.yaml"
        sh 'kubectl get pods -n ddcandi'
        // withKubeConfig([credentialsId: 'K8s']) {
        //     sh 'kubectl apply -f k8s-deployment-candi-prod-test.yaml'
        //     sh 'sleep 120'
        //     sh 'kubectl get pods -n ddcandi'
        // }
        //sh 'cat ./k8s-deployment-candi-prod-test.yaml'
    }
}