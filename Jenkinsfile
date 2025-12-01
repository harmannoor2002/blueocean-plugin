pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Build stage running..."
            }
        }

        stage('Test') {
            steps {
                echo "Testing..."
            }
        }

        stage('Done') {
            steps {
                echo "Pipeline completed successfully!"
            }
        }
    }
}
