
pipeline {
    agent any

    tools {
        nodejs 'NodeJS' // matches the name configured in Global Tools
    }

    environment {
        BUILD_DIR = 'dist'
        DEPLOY_PATH = '/root/hello-world-react'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Suhailakp/hello-world-react-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Project') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    sudo rm -rf $DEPLOY_PATH/*
                    sudo cp -r $BUILD_DIR/* $DEPLOY_PATH/
                '''
            }
        }
    }
}
