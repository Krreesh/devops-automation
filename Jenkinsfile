pipeline {
    agent any
    tools{
        maven 'Maven 3.8.7'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Krreesh/devops-automation.git']])
                sh 'mvn clean install'
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    sh 'docker build -t krreesh/devops-integration .'
                }
            }
        }
        stage('Push image to hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'mydockerpwd', variable: 'MyDockerpwd')]) {
                        sh 'docker login -u krreesh -p ${MyDockerpwd}'
                    }
                    sh 'docker push krreesh/devops-integration'
                }
            }
        }
    }
}