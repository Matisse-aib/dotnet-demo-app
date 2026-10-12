
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

            docker run --rm \
                --network todo_test_network \
                -e ConnectionStrings__TodoDb="Server=todo_test_db;Port=3306;Database=todo_test_db;User=todo_usr;Password=letmeinplz;" \
                dotnet-demo-tests
        '''
    }

    stage('Deploy') {
        sh 'docker compose up -d'
    }

    stage('Verify') {
        sh 'docker compose ps'
    }
}
