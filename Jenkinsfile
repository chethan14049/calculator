pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                echo 'Testing Calculator Application'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t calculator-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker stop calculator-container || true
                    docker rm calculator-container || true
                    docker run -d -p 8081:80 --name calculator-container calculator-app
                '''
            }
        }
    }
}
