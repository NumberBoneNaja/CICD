pipeline {
    agent {
        docker {
            image 'node:18' // ✅ มี npm มาในตัว
        }
    }

    environment {
        FIREBASE_TOKEN = credentials('your-firebase-token-id') // แทนด้วยชื่อจริง
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                sh '''
                    cd frontend
                    npm install
                    npm run build
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // npm test หรือคำสั่งอื่น ๆ ได้ที่นี่
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to Firebase...'
                sh '''
                    cd frontend
                    npm install -g firebase-tools
                    firebase deploy --token "$FIREBASE_TOKEN"
                '''
            }
        }
    }
}
