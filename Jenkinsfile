pipeline {
    agent any
    environment {
        docker=credentials('Docker-Credentials')
    }
    stages {
        stage ('Verifing docker stage') {
            steps {
                sh "docker --version"
            }
        }
        stage ('Building stage') {
            steps {
                sh "docker build -t ${docker_USR}/custom-nginx:${BUILD_ID} ."
                sh 'docker images'
            }
        }
        stage ('Login stage') {
            steps {
                sh "echo ${docker_PSW} | docker login -u ${docker_USR} --password-stdin"
            }
        }
        stage ('Uploading stage') {
            steps {
                sh "docker push velumalai36/custom-nginx:${BUILD_ID}"                
            }
        }
    }
}
