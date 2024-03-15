pipeline {
    agent any // Exécute le pipeline sur n'importe quel agent disponible

    environment {
        // Définir des variables d'environnement si nécessaire
        MAVEN_HOME = '/usr/share/maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code source depuis le SCM configuré
                checkout scm
            }
        }
        
        stage('Compile') {
            steps {
                // Utiliser le shell pour exécuter 'mvn compile'
                sh '${MAVEN_HOME}/bin/mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                // Exécuter les tests unitaires
                sh '${MAVEN_HOME}/bin/mvn test'
            }
        }
        
        stage('Package') {
            steps {
                // Package l'application en un .jar ou .war
                sh '${MAVEN_HOME}/bin/mvn package'
            }
        }
        
        // Ajoutez d'autres étapes selon les besoins de votre pipeline, comme l'analyse de code, le déploiement, etc.
    }

    post {
        // Actions à effectuer après l'exécution du pipeline, comme le nettoyage, l'envoi de notifications, etc.
        always {
            echo 'Le pipeline est terminé.'
        }
        
        success {
            echo 'Le pipeline s\'est terminé avec succès.'
        }
        
        failure {
            echo 'Le pipeline a échoué.'
            // Envoyer une notification en cas d'échec, par exemple
        }
    }
}
