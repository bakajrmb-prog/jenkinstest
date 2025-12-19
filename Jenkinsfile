pipeline {
    agent any

    stages {
        stage('Run tests') {
            steps {
                sh 'pytest test_calculs.py'
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

