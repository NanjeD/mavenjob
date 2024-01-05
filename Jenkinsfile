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
  -Dsonar.projectKey=new-job \
  -Dsonar.projectName='new-job' \
  -Dsonar.host.url=http://54.82.101.204:9000 \
  -Dsonar.token=sqp_dce912479468ceaede6c9b84077400e133968204"
      }
    }
  }
}
