@Library('my-shared-library') _
pipeline {
    agent any
        
    environment {
        DOCKERHUB_CRED=credentials('dockerhub-registry-credentials')
    }
    stages {
        stage('Set Environment') {
            steps {
                script {
                    REGISTRY = "ersinsari"
                    REPOSITORY = "docker-build-push"
                }
            }
        }
        stage('Hello') {
            steps {
                sayHello "hepapi"
            }
        }
        stage('Build') {
            steps {
                dockerBuild "${REGISTRY}", "${REPOSITORY}"
            }
        }
        stage('Push') {
            steps {
                dockerPush "${REGISTRY}", "${REPOSITORY}"
            }
        }
    }
}