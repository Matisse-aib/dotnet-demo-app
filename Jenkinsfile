node {
    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        sh 'docker compose build'
    }

stage('Test') {
    sh '''
        docker build -t dotnet-demo-tests -f TodoApp.Tests/Dockerfile .
        docker run --rm dotnet-demo-tests
    '''
}

    stage('Deploy') {
        sh 'docker compose up -d'
    }

    stage('Verify') {
        sh 'docker compose ps'
    }
}