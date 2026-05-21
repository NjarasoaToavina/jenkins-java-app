pipeline {

    agent any

    tools {
        maven 'Maven3'
    }

    environment {
        IMAGE_NAME = "njarasoatoavina/app-java:1.0"
    }

    stages {

        stage('Git Checkout') {

            steps {
                git branch: 'main',
                url: 'https://github.com/njarasoatoavina/jenkins-java-app.git'
            }
        }

        stage('Compile') {

            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Unit Test Execution') {

            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {

            steps {
                sh 'mvn package'
            }
        }

        stage('Build Docker Image') {

            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }
    }

    post {

        success {
            echo 'Build réussi'
        }

        failure {
            echo 'Build échoué'
        }
    }
}
