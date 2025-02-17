pipeline {
    agent any
    environment {
        DOCKER_USERNAME=credentials('Docker-username')
        DOCKER_PASSWORD=credentials('Docker-password')
    }
    stages {
        stage ('Verifing docker stage') {
            steps {
                sh "docker --version"
            }
        }
        stage ('Building stage') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    sh 'docker ps'
                    sh 'docker build -t velumalai36/custom-nginx:1.0 .'
                    sh 'docker images'
                }
            }
        }
        stage ('Login stage') {
            steps {
                sh "echo ${DOCKER_PASSWORD} | docker login -u ${DOCKER_USERNAME} --password-stdin"
                sh 'echo Logged in successfully'
            }
        }
        stage ('Uploading stage') {
            steps {
                sh "docker push velumalai36/custom-nginx:${BUILD_ID}"                
            }
        }
    }
}
