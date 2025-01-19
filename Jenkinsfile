pipeline {
    agent any

    stages {
        stage('Build docker image') {
            steps {
                bat 'docker builtd -t ml_project/frontend .'
            }
        }
        stage('tag buitd image') {
            steps {
                bat 'docker tag ml_project ibouaida/ml_project:v1 .'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Teste le deployement vers enrovironnement de production'
            }
        }
    }
}
