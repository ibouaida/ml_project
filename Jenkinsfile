pipeline {
    agent any
    environment {
        BACKEND_IMAGE = 'ibouaida/ml_project_backend'
        FRONTEND_IMAGE = 'ibouaida/ml_project_frontend'
        DOCKERHUB_CREDENTIALS = 'docker-hub-credentials'
    }
    stages {
        stage('Cloner le dépôt') {
            steps {
                git branch: 'main', url: 'https://github.com/ibouaida/ml_project.git/ml_project.git'
            }
        }
}
