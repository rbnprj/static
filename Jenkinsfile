pipeline {
     agent any
     stages {
         stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
         stage('Upload to AWS') {
            steps {
                withAWS(region:'us-east-1', credentials:'aws-static') {
                    sh 'echo "Hello World with AWS creds"'
                    s3Upload(bucket:"pipeline-s2", includePathPattern:'**/*');
                }
            }
        }
     }
}