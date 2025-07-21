pipeline {
    agent any

    environment {
        FLUTTER_HOME = "C:\\flutter"
        PATH = "${env.FLUTTER_HOME}\\bin;${env.PATH}"
    }

    stages {
        stage('Clone Repo') {
            steps {
                echo "Cloning repo"
                git 'https://github.com/Thaanees-RM/my-flutter-app.git'
            }
        }

        stage('Flutter Clean') {
            steps {
                bat 'flutter clean'
            }
        }

        stage('Get Dependencies') {
            steps {
                bat 'flutter pub get'
            }
        }

        stage('Build APK') {
            steps {
                bat 'flutter build apk'
            }
        }

        stage('Archive APK') {
            steps {
                archiveArtifacts artifacts: '**\\build\\app\\outputs\\flutter-apk\\app-release.apk', fingerprint: true
            }
        }
    }
}
