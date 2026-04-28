pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Mayookha05/Moneymap.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'C:\\Users\\retna\\AppData\\Local\\Python\\bin\\python.exe -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'C:\\Users\\retna\\AppData\\Local\\Python\\bin\\python.exe manage.py test --verbosity=2'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t moneymap .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker-compose down'
                bat 'docker-compose up -d --build'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}