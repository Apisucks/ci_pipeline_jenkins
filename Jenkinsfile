pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World from Repo'
                sh "ctag=`git tag --sort=-committerdate | head -1`
                git checkout $ctag"
            }
        }
        stage('Build') {
            steps {
                echo 'Build in progress from Repo'    
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy in progress from Repo'    
            }
        }
    }
}