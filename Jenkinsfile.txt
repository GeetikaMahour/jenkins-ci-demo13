pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting source code from GitHub'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Python application'
                bat 'python --version'
                bat 'python app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests'
                bat 'python -m unittest -v test_app.py'
            }
        }

    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
