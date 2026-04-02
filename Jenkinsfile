pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'git@github.com:08pradeep/flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop flask-app || true'
                sh 'docker rm flask-app || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name flask-app flask-app'
            }
        }
    }
}
