pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
            }
        }
        stage('Build') {
            steps {
                echo 'Building Calculator with Maven...'
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Running Tests...'
                bat 'mvn test'
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging...'
                bat 'mvn package -DskipTests'
            }
        }
    }
    post {
        success {
            echo 'BUILD SUCCESS!'
        }
        failure {
            echo 'BUILD FAILED - Check logs'
        }
    }
}
