pipeline {
  agent any
  tools{
    maven 'Maven'
   }
  stages {
    stage ("build jar") {
      steps {
        script {
          echo "building the application..."
          sh 'mvn package'
        }
      }
    } 
    stage ("build image") {
      steps {
        script {
          echo "building the docker image..."
          withCredentials([UsernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]){
               sh 'docker build -t uday0456/demo-app:jma-2.0 .'
               sh "echo $PASS | docker login -u $USER --password-stdin"
               sh 'docker push uday0456/demo-app:jma-2.0'
          }
        }
      }
    }
     stage ("test") {
      steps {
        echo 'test the application...'
      }
    }
     stage ("deploy") {
      steps {
        echo 'deploying the application...'
      }
    }
    post {
      always {
        
        
  }
}

