
pipeline {
    agent any

    stages {
        stage('Run tests') {
            steps {
                sh 'python3 test_calculs.py'
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

