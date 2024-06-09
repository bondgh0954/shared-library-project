#!/user/bin/env groovy
@Library('shared-library')
def gv
pipeline{
  agent any
  tools{
    maven 'maven-3'
  }

  stages{

    stage('init'){
      steps{
        script{
          gv = load 'script.groovy'
        }
      }
    }


    stage('buildJar'){
      steps{
        script{
          buildJar()
        }
      }
    }
    stage('buildImage'){
      steps{
        script{
          buildImage 'nanaot/java-app:8.7'
          dockerLogin()
          pushImage 'nanaot/java-app:8.7'
        }
      }
    }

  }
}