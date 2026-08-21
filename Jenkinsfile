pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '"C:\\Users\\hu\\AppData\\Local\\Python\\bin\\python.exe" -m pip install pytest'
            }
        }

        stage('Test') {
            steps {
                bat '"C:\\Users\\hu\\AppData\\Local\\Python\\bin\\python.exe" -m pytest'
            }
        }
    }
}