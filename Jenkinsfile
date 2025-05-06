pipeline {
    agent any
    environment {
        FIREBASE_TOKEN = credentials('c77f1ccf-b9b3-4337-8fb5-1b0b22f36f31') // ใช้ ID จาก Jenkins Credentials
    }
    stages {
        
        stage('Build') {
            steps {
                echo "Building project..."
                dir('frontend') {
                    sh '''
                        npm install
                        npm run build
                    '''
                }
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
                
                dir('frontend') {
                    sh 'npm install firebase-tools --save-dev'
                    sh "firebase deploy --token $FIREBASE_TOKEN"
                }
            }
        }

        

    }
}
