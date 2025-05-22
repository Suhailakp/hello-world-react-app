pipeline {
    agent any

    tools {
        nodejs 'NodeJS'  // Make sure "node18" is configured in Jenkins Global Tools
    }

    environment {
        REPO_URL = 'https://github.com/Suhailakp/hello-world-react-app.git'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git url: "${REPO_URL}", branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            when {
                expression { fileExists('build') || fileExists('dist') }
            }
            steps {
                echo 'Deploy step placeholder – upload to server, move to Nginx folder, etc.'
                // Example: sh 'scp -r build/ user@yourserver:/var/www/html'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}

