pipeline {
    agent any

    stages {
        stage("Dummy") {
            steps{
                echo "Dummy"
            }
        }

        stage("Build") {
            steps{
                echo "building"
            }
        }
        
        stage("Test") {
            steps {
                echo "testing"
            }
        }

        stage("Deploy") {
            steps{
                echo "deploying"
            }
        }
    }
}