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
  -Dsonar.projectKey=nanje-demo \
  -Dsonar.projectName='nanje-demo' \
  -Dsonar.host.url=http://ec2-3-86-238-50.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_dccd1c306f8ebb0aa849050b2008b54008f1b3e3"
      }
    }
  }
}
