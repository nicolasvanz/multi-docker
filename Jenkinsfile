pipeline {
    agent any

    stages {
        stage("Build Client") {
            steps{
                sh "docker build -t nicolasvanz/react-test -f ./client/Dockerfile.dev ./client"
            }
        }
        
        stage("Run Client") {
            steps {
                sh "docker run -e CI=true nicolasvanz/react-test npm test -- --coverage"
            }
        }

        stage("Build production images") {
            steps{
                sh "docker build -t nicolasvanz/multi-client ./client"
                sh "docker build -t nicolasvanz/multi-nginx ./nginx"
                sh "docker build -t nicolasvanz/multi-server ./server"
                sh "docker build -t nicolasvanz/multi-worker ./worker"
            }
        }

        stage("Push production images") {
            steps {
                withDockerRegistry([
                    credentialsId: "dockerhub",
                    url: ""
                ]) {
                    sh "docker push nicolasvanz/multi-client"
                    sh "docker push nicolasvanz/multi-nginx"
                    sh "docker push nicolasvanz/multi-server"
                    sh "docker push nicolasvanz/multi-worker"
                }
            }
        }
    }
}