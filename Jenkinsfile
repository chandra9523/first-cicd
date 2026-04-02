pipeline {
    agent any

    stages {

        stage('Run Tests inside Docker') {
            steps {
                sh '''
                docker run --rm -v $(pwd):/app -w /app python:3.9 \
                sh -c "pip install -r requirements.txt && pytest"
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f myapp-container || true
                docker run -d -p 5000:5000 --name myapp-container myapp
                '''
            }
        }
    }
}