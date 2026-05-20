pipeline {
 agent any

 stages {

  stage('Build') {
   steps {
    sh 'docker build -t devops-app .'
   }
  }

  stage('Deploy') {
   steps {
    sh '''
    docker stop app || true
    docker rm app || true
    docker run -d --name app -p 8081:80 devops-app
    '''
   }
  }

 }

}