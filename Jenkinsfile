pipeline {
    agent any

    stages {
        // Étape 1 : construire l'image Docker
        stage('Build Docker image') {
            steps {
                sh 'docker build -t my-python-app:latest .'
            }
        }

        // Étape 2 : exécuter les tests dans le conteneur Docker
        stage('Run tests') {
            steps {
                sh 'docker run --rm my-python-app pytest --junitxml=report.xml'
            }
        }

        // Étape 3 (optionnel) : pousser l'image Docker si les tests réussissent
        stage('Push Docker image') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                sh 'docker tag my-python-app:latest my-registry/my-python-app:1.0.0'
                sh 'docker push my-registry/my-python-app:1.0.0'
            }
        }
    }

    post {
        // Affichage des résultats des tests dans Jenkins
        always {
            junit 'report.xml'
        }
        success {
            echo 'Pipeline terminé avec succès !'
        }
        failure {
            echo 'Pipeline échoué !'
        }
    }
}

