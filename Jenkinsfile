node {
    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        sh 'docker compose build'
    }

    stage('Deploy') {
        sh 'docker compose up -d'
    }

    stage('Verify') {
        sh 'docker compose ps'
    }
}