pipeline {
    agent any
    tools { maven 'Maven' } // Jenkins tool name
    stages {
        stage('Checkout') {
            steps { 
                git url: 'git@github.com:harmannoor2002/blueocean-plugin.git', 
                    credentialsId: 'github-ssh', branch: 'master' 
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // Set Maven path
                    def mvnHome = tool 'Maven'
                    env.PATH = "${mvnHome}\\bin;${env.PATH}"
                }
                // Set Python path and run Maven build
                withEnv(['PYTHON=C:\\Python313\\python.exe']) {
                    bat 'mvn -B -DskipTests clean package'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                bat 'if not exist C:\\deploy mkdir C:\\deploy'
                bat 'copy /Y target\\*.war C:\\deploy\\'
            }
        }
    }
    
    post {
        always { 
            echo "Finished build ${currentBuild.fullDisplayName}" 
        }
    }
}
