pipeline {

    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/chandra9523/first-cicd.git'
            }
        }

        
        

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t chandra9523/first-cicd:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push cbdocker2525/first_cicd:latest'
            }
        }

    
    }
}