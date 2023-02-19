pipeline {
    agent any
    environment {
        dockerhub=credentials('dockerhub')
    }
    stages {
        stage('git_checckout') {
            steps {
                git branch: 'main', url: 'https://github.com/ARUNBABU99/kubernetes_sample_project.git'
            }
        }
        stage('Docker_build') {
            steps {
                sh 'sudo docker build -t test .'
            }
        }
        stage('Dockerimages') {
            steps {
                sh 'sudo docker images'
            }
        }
        stage('Docker_push') {
            steps {
                sh 'sudo docker tag test arunbabu01/test'
                sh 'docker login -u $dockerhub_USR -p $dockerhub_PSW'
                sh 'sudo docker push arunbabu01/test'
            }
        }
    }
}
