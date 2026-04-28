pipeline {
    agent any

    environment {
        PYTHON = 'py'
    }

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'master', url: 'https://github.com/Mayookha05/Moneymap.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'py -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'py manage.py test --verbosity=2'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t moneymap .'
            }
        }

        stage('Deploy') {
            steps {
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