pipeline {
    agent any
    stages {
        stage ('Verifing docker stage') {
            steps {
                sh "docker --version"
            }
        }
        stage ('Building stage') {
            timeout(time: 1, unit: 'HOURS') {
                steps {
                    sh 'docker ps'
                    sh 'docker build -t velumalai36/custom-nginx:1.0 .'
                    sh 'docker images'
                }
            }
        }
    }
}
