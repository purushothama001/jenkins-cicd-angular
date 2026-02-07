pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        sh '''
          node -v
          npm -v
          npm install
          npm run build
        '''
      }
    }
  }
}

        stage('S3 Upload') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'f8d26d06-17e2-46f9-a816-c88ca0f07be0) {
                    sh 'ls -la'
                    sh 'aws s3 cp dist/angular-tour-of-heroes/browser/. s3://jenkins-bucket-angular/ --recursive'
                }
            }
        }
    }
}
