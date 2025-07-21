pipeline {
    agent any

    environment {
        ANDROID_HOME = "/usr/lib/android-sdk"
        PATH = "${env.PATH}:${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/platform-tools"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Thaanees-RM/my-flutter-app.git'
            }
        }

        stage('Install Flutter') {
            steps {
                sh '''
                    if [ ! -d "flutter" ]; then
                        git clone https://github.com/flutter/flutter.git -b stable
                    fi
                    export PATH="$PATH:$PWD/flutter/bin"
                    flutter doctor
                '''
            }
        }

        stage('Get Dependencies') {
            steps {
                sh '''
                    export PATH="$PATH:$PWD/flutter/bin"
                    flutter pub get
                '''
            }
        }

        stage('Build APK') {
            steps {
                sh '''
                    export PATH="$PATH:$PWD/flutter/bin"
                    flutter build apk
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/build/app/outputs/flutter-apk/app-release.apk', allowEmptyArchive: true
        }
    }
}
o

