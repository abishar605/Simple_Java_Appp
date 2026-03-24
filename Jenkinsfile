pipeline {
    agent any

    stages {

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t AbishaR26/java-app:latest .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker login -u AbishaR26 -p AbishaR@2005'
                sh 'docker push AbishaR26/java-app:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
