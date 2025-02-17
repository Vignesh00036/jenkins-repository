pipeline {
    agent any
    stages {
        stage ('Verifing docker stage') {
            steps {
                sh "docker --version"
            }
        }
        stage ('Building stage') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    sh "docker build -t velumalai36/custom-nginx:${BUILD_ID} ."
                    sh 'docker images'
                }
            }
        }
        stage ('Login stage') {
            steps {
                sh "echo @Beast00036@ | docker login -u velumalai36 --password-stdin"
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
