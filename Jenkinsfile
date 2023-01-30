pipeline {
    agent any
    tools {maven 'Maven 3.8.7'}
  stages{
      stage('Git checkout'){
        steps{
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Krreesh/devops-automation.git']])
            script { sh 'mvn clean install' }
        }
    }
    stage('Build docker image'){
        steps{
           script { sh 'docker build -t krreesh/devops-integration:v1 .' }
        }
    }
    stage('Push image to hub'){
        steps{
            withCredentials([string(credentialsId: 'dockerpass', variable: 'mydockerpwd')]) {
            sh 'docker login -u krreesh -p ${mydockerpwd}'
            }
             sh 'docker push krreesh/devops-integration:v1' 
        }
    }
  }
}