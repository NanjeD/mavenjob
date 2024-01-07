pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-cloning project repo'){
      steps{
        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'maven build', url: 'https://github.com/etechDevops/etech-mavenApp.git']])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
        stage('codequality'){
        steps{
       sh "mvn clean verify sonar:sonar \
  -Dsonar.projectKey=demo-sonar \
  -Dsonar.projectName='demo-sonar' \
  -Dsonar.host.url=http://ec2-54-86-33-207.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_a885e74d018b56d0a07caca83722756f5048c2ca"
      }
    }
  }
}
