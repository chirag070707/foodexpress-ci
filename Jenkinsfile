pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '"C:\\Users\\hu\\AppData\\Local\\Python\\bin\\python.exe" -m venv venv'
                bat 'call venv\\Scripts\\activate && python -m pip install pytest flake8'
            }
        }

        stage('Code Quality') {
            steps {
                bat 'call venv\\Scripts\\activate && flake8 cart.py orders.py || exit /b 0'
            }
        }

        stage('Test') {
            steps {
                bat 'call venv\\Scripts\\activate && pytest'
            }
        }

        stage('Package') {
            steps {
                bat 'call venv\\Scripts\\activate && python package.py'
                archiveArtifacts artifacts: 'foodexpress.zip', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: all stages passed and the artifact was created.'
        }

        failure {
            echo 'FAILURE: one stage failed. Open the red stage to see why.'
        }
    }
}