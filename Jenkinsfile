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
       sh ""mvn clean verify sonar:sonar \
  -Dsonar.projectKey=free-sonar \
  -Dsonar.projectName='free-sonar' \
  -Dsonar.host.url=http://34.239.253.145:9000 \
  -Dsonar.token=sqp_815bccc09971000eafe8c88b6846b4a090640659
      }
    }
  }
}
