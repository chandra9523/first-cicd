pipeline {

    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/chandra9523/first-cicd.git'
            }
        }

        stage('Setup Python Environment') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                . venv/bin/activate
                python app.py
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }
        

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t chandra9523/first-cicd:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push cbdocker2525/first-ci-cd:latest'
            }
        }

    
    }
}