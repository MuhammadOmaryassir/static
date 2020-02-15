pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "hello World"'
        sh '''
          echo "multiline shell steps works too"
          ls -lah
        '''
      }
    }
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Upload to AWS S3') {
      steps {
        withAWS(region:'us-west-1',credentials:'Static HTML publisher in AWS') {
		      sh 'echo "Hello World with AWS"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkinstestmuhmmadomar')
              }
            }
    }
  }
}