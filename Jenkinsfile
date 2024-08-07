pipeline {
    agent {
        dockerContainer {
            image 'python:3.12.4-alpine3.20'
        }
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Your test steps here
            }
        }
    }
}
