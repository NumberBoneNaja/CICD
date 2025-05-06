pipeline {
    agent any

    environment {
        FIREBASE_TOKEN = credentials('c77f1ccf-b9b3-4337-8fb5-1b0b22f36f31')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building project..."
                dir('frontend') {
                    sh 'npm install'
                }
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // ถ้ามี test script ใน package.json
                // dir('frontend') {
                //     sh 'npm run test'
                // }
            }
        }

        stage('Deploy') {
            steps {
                dir('frontend') {
                    echo "Deploying to Firebase Hosting..."
                    sh 'npm install -g firebase-tools' // หรือใช้ npx
                    sh "firebase deploy --only hosting --token $FIREBASE_TOKEN"
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished"
        }
        success {
            echo "✅ Deployment success!"
        }
        failure {
            echo "❌ Deployment failed!"
        }
    }
}
