pipeline {
    agent none // forces each step to set it's own agent

    stages {
        stage("Build Client") {
            agent any
            steps{
                echo "[+] Building client docker image"
                sh "docker build -t nicolasvanz/react-test -f ./client/Dockerfile.dev ./client"
            }
        }
        
        stage("Run Client") {
            agent any
            steps {
                echo "[+] Running client docker image"
                sh "docker run -e CI=true nicolasvanz/react-test npm test -- --coverage"
            }
        }

        stage("Deploy") {
            agent any
            steps{
                echo "deploying"
            }
        }
    }
}