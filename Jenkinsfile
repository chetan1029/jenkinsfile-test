pipeline {
    agent any
    environment { 
        jk_name = 'jk testing'
        TEST_SECRET = credentials('testing-sceret-text')
    } 
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!'
                echo "Test Secret ${env.TEST_SECRET}"
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