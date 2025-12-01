pipeline {
    agent any
    tools {
        nodejs 'NodeJS_24'       // Replace with your NodeJS installation name in Jenkins
        python 'Python_3.13'     // Replace with your Python installation name in Jenkins
        maven 'Maven_3.9'        // Replace with your Maven installation name in Jenkins
    }
    environment {
        PATH = "${tool 'NodeJS_24'}/bin:${tool 'Python_3.13'}/bin:${tool 'Maven_3.9'}/bin:${env.PATH}"
    }
    stages {
        stage('Build') {
            steps {
                echo "PATH is ${env.PATH}"
                sh 'node -v'
                sh 'python --version'
                sh 'mvn -v'
            }
        }
    }
}
