pipeline {
    agent any

    environment {
        PATH = "/home/thaanees/flutter/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Thaanees-RM/my-flutter-app.git'
            }
        }

        stage('Flutter Doctor') {
            steps {
                sh 'flutter doctor'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'flutter pub get'
            }
        }

        stage('Build Android APK') {
            steps {
                sh 'flutter build apk --release'
            }
        }

        stage('Build Web App') {
            steps {
                sh 'flutter build web'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/app/outputs/flutter-apk/app-release.apk', fingerprint: true
                archiveArtifacts artifacts: 'build/web/**', fingerprint: true
            }
        }
    }

    post {
        always {
            echo '✅ Build Completed'
        }
    }
}
