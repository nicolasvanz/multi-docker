pipeline {
    agent any

    stages {
        stage("Dummy") {
            steps{
                echo "dummy"
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