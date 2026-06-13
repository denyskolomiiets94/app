pipeline {
    agent {
        label 'worker1'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-app:test .'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run --rm node-app:test'
            }
        }
    }

    post {
        failure {
            echo 'Tests failed'
        }
    }
}