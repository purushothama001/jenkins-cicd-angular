pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        sh 'ls'
        sh 'npm install'
        sh 'echo N | ng analytics off'
        sh 'ng build'
        sh 'ls'
        sh 'cd dist && ls'
        sh 'cd dist/angular-tour-of-heroes/browser && ls'
      }
    }

    stage('S3 Upload') {
      steps {
        withAWS(region: 'us-east-1', credentials: 'f8d26d06-17e2-46f9-a816-c88ca0f07be0') {
          sh 'ls -la'
          sh 'aws s3 cp dist/angular-tour-of-heroes/browser/. s3://jenkins-bucket-angular/ --recursive'
        }
      }
    }
  }
}
``
