pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -f dockerfile . -t yaraamrallah/jenkins_node:v1.0'
            }
        }
        stage('push') {
            steps {
                withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:USERNAME,passwordVariable:PASSWORD)]){
                withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:"USERNAME",passwordVariable:"PASSWORD")]){
                sh 'docker login --username $USERNAME --password $PASSWORD'
                sh 'docker push yaraamrallah/jenkins_node:v1.0'
            }
