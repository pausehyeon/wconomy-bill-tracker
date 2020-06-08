pipeline {
    environment {
        workDirectory = "billtracker"
        dockerFilePath = "https://raw.githubusercontent.com/pausehyeon/devops-environment/master/java/v1/Dockerfile"
        registry = "pausehyeon/billtracker"
        registryCredential = "docker-hub"
    }
    agent any
    stages {
        stage('Checkout Source Code') {
            steps {
                checkout scm
            }
        }        
        stage('Prepare') {
            steps {
                dir('${workDirectory}') {
                    sh 'pwd'
                    sh 'chmod +x ./gradlew'
                    sh 'ls'
                }
            }
        }
        stage('Build Jar') {
            steps {
                dir('${workDirectory}') {
                   sh './gradlew build'
                }
            }
        }
        stage('Build docker image') {
            steps {
                sh 'curl -s $dockerFilePath --output Dockerfile'
                sh 'docker build -t $registry:latest .'
            }
        }
        stage('Deploy docker image') {
            steps {
                withDockerRegistry([ credentialsId: registryCredential, url: "" ]) {
                    sh 'docker push $registry:latest'
                }
            }
        }
        /*
        stage('Clean docker image') {
            steps{
                sh "docker rmi $registry"
            }
        }
        */
     }
}
