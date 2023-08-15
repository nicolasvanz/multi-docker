pipeline {
    agent none // forces each step to set it's own agent

    stages {
        stage("Build Client") {
            agent any
            steps{
                sh "docker build -t nicolasvanz/react-test -f ./client/Dockerfile.dev ./client"
            }
        }
        
        stage("Run Client") {
            agent any
            steps {
                sh "docker run -e CI=true nicolasvanz/react-test npm test -- --coverage"
            }
        }

        stage("Build production images") {
            agent any
            steps{
                sh "docker build -t nicolasvanz/multi-client ./client"
                sh "docker build -t nicolasvanz/multi-nginx ./nginx"
                sh "docker build -t nicolasvanz/multi-server ./server"
                sh "docker build -t nicolasvanz/multi-worker ./worker"
            }
        }
    }
}