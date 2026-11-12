pipeline {
    agent any
    stages {
        stage('Setup Maven') {
            steps {
                echo 'Setting up Maven automatically...'
                bat '''
                if not exist C:\\maven\\apache-maven-3.9.9\\bin\\mvn.cmd (
                    powershell -Command "New-Item -ItemType Directory -Force -Path C:\\maven; Invoke-WebRequest -Uri https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.zip -OutFile C:\\maven\\maven.zip; Expand-Archive -Path C:\\maven\\maven.zip -DestinationPath C:\\maven -Force"
                )
                C:\\maven\\apache-maven-3.9.9\\bin\\mvn.cmd -version
                '''
            }
        }
        stage('Build') {
            steps {
                echo 'Building Calculator with Maven...'
                bat 'C:\\maven\\apache-maven-3.9.9\\bin\\mvn.cmd clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Running Tests...'
                bat 'C:\\maven\\apache-maven-3.9.9\\bin\\mvn.cmd test'
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging...'
                bat 'C:\\maven\\apache-maven-3.9.9\\bin\\mvn.cmd package -DskipTests'
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
