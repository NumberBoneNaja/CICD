pipeline {
    agent any

    environment {
        FIREBASE_TOKEN = credentials('c77f1ccf-b9b3-4337-8fb5-1b0b22f36f31')
    }

    stages {
        stage('Clone') {
            steps {
                echo "Cloning repo..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building project..."
                dir('frontend') {
                    sh 'pwd'
                    sh 'ls -la'
                    sh 'npm install'
                }
            }
        }


        stage('Test') {
            steps {
                echo "Running tests..."
                // ถ้ามี test script ใน package.json ก็ใส่ได้ เช่น:
                // dir('frontend') {
                //     sh 'npm run test'
                // }
            }
        }

        stage('Deploy') {
            steps {
                dir('frontend') {
                    echo "Deploying to Firebase Hosting..."
                    sh 'npm install -g firebase-tools'
                    sh "firebase deploy --only hosting --token $FIREBASE_TOKEN"
                }
            }
        }
    }
}
