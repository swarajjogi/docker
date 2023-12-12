pipeline {
    agent any

    stages {
        stage('Build app') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/swarajjogi/docker.git']])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t jenkinsdocker .'
                }
            }
        }

        stage('Rename Image Tag') {
            steps {
                script {
                    bat 'docker tag jenkinsdocker swarajjogi/jenkinsdockerapp:image1'
                }
            }
        }

        stage('Push Image to docker Hub') {
            steps {
                script {
                    bat 'docker login -u swarajjogi -p Pass@1234'
                    bat 'docker push swarajjogi/jenkinsdockerapp:image1'
                }
            }
        }
    }
}
