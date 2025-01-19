pipeline {
    agent any
    environment {
        BACKEND_IMAGE = 'ibouaida/ml_project_backend'   // Nom de l'image Docker pour le backend
        FRONTEND_IMAGE = 'ibouaida/ml_project_frontend' // Nom de l'image Docker pour le frontend
        DOCKERHUB_CREDENTIALS = 'docker-hub-credentials'
    }
    stages {
        stage('Cloner le dépôt') {
            steps {
                git branch: 'main', url: 'https://github.com/ibouaida/ml_project.git'
            }
        }

        stage('Construire les images Docker') {
            parallel {
                stage('Backend') {
                    steps {
                        script {
                            docker.build("${BACKEND_IMAGE}", "./backend")
                        }
                    }
                }
                stage('Frontend') {
                    steps {
                        script {
                            docker.build("${FRONTEND_IMAGE}", "./frontend")
                        }
                    }
                }
            }
        }

        stage('Pousser les images sur Docker Hub') {
            parallel {
                stage('Pousser Backend') {
                    steps {
                        script {
                            docker.withRegistry('https://index.docker.io/v1/', "${DOCKERHUB_CREDENTIALS}") {
                                docker.image("${BACKEND_IMAGE}").push("${env.BUILD_ID}")
                            }
                        }
                    }
                }
                stage('Pousser Frontend') {
                    steps {
                        script {
                            docker.withRegistry('https://index.docker.io/v1/', "${DOCKERHUB_CREDENTIALS}") {
                                docker.image("${FRONTEND_IMAGE}").push("${env.BUILD_ID}")
                            }
                        }
                    }
                }
            }
        }
    }
}
