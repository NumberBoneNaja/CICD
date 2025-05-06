pipeline {
    agent any
    environment {
        FIREBASE_TOKEN = credentials('c77f1ccf-b9b3-4337-8fb5-1b0b22f36f31') // ใช้ ID จาก Jenkins Credentials
    }
    stages {
           stage('Clone') {
            steps {
                git 'https://github.com/NumberBoneNaja/CICD.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building project..."
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying..."
                sh "npx firebase deploy --token $FIREBASE_TOKEN"
            }
        }

        

    }
}
