
pipeline{
  agent any
  tools{
    maven 'maven-3'
  }

  stages{


    stage('buildJar'){
      steps{
        script{
          echo 'building jar file from the application'
          sh 'mvn package'
        }
      }
    }
    stage('buildImage'){
      steps{
        script{
          echo 'building docker image from the application'
          withCredentials([usernamePassword(credentialsId:'dockerhub-credentials',usernameVariable:'USER',passwordVariable:'PASSWORD')]){
            sh "docker build -t nanaot/java-app:5.4 ."
            sh "echo $PASSWORD | docker login -u $USER --password-stdin"
            sh "docker push nanaot/java-app:5.4"
          }
        }
      }
    }

  }
}