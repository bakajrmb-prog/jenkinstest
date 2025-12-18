pipeline {
    agent any

    stages {
        stage('Clone GitHub') {
            steps {
                git url: 'https://github.com/wafaroukhmi-tech/my-python.git', branch: 'main'
            }
        }

        stage('Run Python') {
            steps {
                sh 'python3 main.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminé avec succès !'
        }
        failure {
            echo 'Pipeline échoué !'
        }
    }
}

