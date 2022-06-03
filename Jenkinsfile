pipeline {
    agent any
    environment { 
        jk_name = 'jk testing'
    } 
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!' 
                sh 'printenv'
            }
        }
        stage('stage 2') {
            environment { 
                jk_stage = 'jk stage 2'
            } 
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                sh 'printenv'
            }
        }
    }
}