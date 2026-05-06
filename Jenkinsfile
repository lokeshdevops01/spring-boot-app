pipeline {
    agent any	

    stages {

        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t spring-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f spring-container || true'
                sh 'docker run -d -p 8081:8080 --name spring-container spring-app'
            }
        }
    }
}
