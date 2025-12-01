pipeline {
    agent any

    environment {
        // If you have Maven installed via Jenkins global tools
        MAVEN_HOME = tool name: 'Maven_3.9', type: 'maven'
        PATH = "${env.MAVEN_HOME}/bin;${env.PATH}"

        // Use system Node and Python
        NODE_HOME = "C:\\Program Files\\nodejs"
        PATH = "${env.NODE_HOME};${env.PATH}"

        PYTHON_HOME = "C:\\Python313"
        PATH = "${env.PYTHON_HOME};${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Clean old node_modules just in case
                    bat 'rmdir /s /q jenkins-design-language\\node_modules || echo Node modules not found'
                    bat 'npm cache clean --force'

                    // Build with Maven, skip tests
                    bat 'mvn -B -DskipTests clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Skipping deploy since this is just a CI build."
            }
        }
    }

    post {
        always {
            echo "Finished Jenkins build"
        }
        failure {
            echo "Build failed. Check logs for errors."
        }
    }
}
