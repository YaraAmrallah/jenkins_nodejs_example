pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -f dockerfile . -t yaraamrallah/jenkins_node_dev:v1.0'
            }
        }
        stage('push') {
            steps {
                withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:"USERNAME",passwordVariable:"PASSWORD")]){
                sh 'docker login --username $USERNAME --password $PASSWORD'
                sh 'docker push yaraamrallah/jenkins_node_dev:v1.0'
            }

            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 4000:3000 yaraamrallah/jenkins_node_dev:v1.0'
            }
        }
    }
}
