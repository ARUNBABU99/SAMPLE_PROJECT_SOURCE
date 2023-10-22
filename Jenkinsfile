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
                sh ' docker build -t test .'
            }
        }
        stage('Dockerimages') {
            steps {
                sh ' docker images'
            }
        }
        stage('Docker_push') {
            steps {
                sh ' docker tag test arunbabu01/test'
                sh 'docker login -u $dockerhub_USR -p $dockerhub_PSW'
                sh ' docker push arunbabu01/test'
            }
        }
    }
}
