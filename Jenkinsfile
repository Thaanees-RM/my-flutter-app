pipeline {
  agent any

  environment {
    PATH = "${env.PATH}:/home/ubuntu/flutter/bin"
  }

  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/Thaanees-RM/my-flutter-app.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'flutter pub get'
      }
    }

    stage('Build Web') {
      steps {
        sh 'flutter build web'
      }
    }

    stage('Deploy to Nginx') {
      steps {
        sh '''
          sudo rm -rf /var/www/html/*
          sudo cp -r build/web/* /var/www/html/
          sudo systemctl restart nginx
        '''
      }
    }
  }
}
