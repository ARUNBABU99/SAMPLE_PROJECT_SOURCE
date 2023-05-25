library identifier: 'jenkins_shared_libs@main',
    // 'main' refers to a valid git ref (branch)
    retriever: modernSCM([
      $class: 'GitSCMSource',
      remote: 'https://github.com/ARUNBABU99/Jenkins_shared_libs.git'
])

pipeline {
    agent {
        docker {
            image 'docker'
            args  '-u root:root --network host -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('git_checckout') {
            steps {
                git branch: 'main', url: 'https://github.com/ARUNBABU99/kubernetes_sample_project.git'
            }
        }
        stage('Docker_build') {
            steps {
                sh 'docker build -t test .'
            }
        }
        stage('Dockerimages') {
            steps {
                sh 'docker images'
            }
        }
        stage('Docker_push') {
            steps {
                login('test')
                // sh 'docker tag test arunbabu01/test'
                // sh 'docker login -u $dockerhub_USR -p $dockerhub_PSW'
                // sh 'docker push arunbabu01/test'
            }
        }
    }
}
