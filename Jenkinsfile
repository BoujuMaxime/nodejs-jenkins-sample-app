pipeline {
    agent any

    tools { 
        nodejs "Default" 
    }
    
    environment {
        DOCKER_IMAGE = "jenkins-demo-app"
        DOCKER_TAG = "${BUILD_NUMBER}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install '
            }
        }
        
        stage('Run Tests') {
            // TODO: Lancer les tests
            steps {
                sh 'npm test'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} .'
            }
        }
        
        stage('Deploy') {
            // TODO: Déployer le conteneur
            // Arrêter l'ancien conteneur s'il existe 
            // Démarrer le nouveau conteneur avec la nouvelle version
            steps {
                sh 'docker compose down'
                sh 'docker compose up -d --buid'
            }
        }
    }
    
    //post {
        // TODO: Partie bonus
    //}
}
