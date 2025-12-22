pipeline {
    agent any
 
    environment {
        BACKEND_IMAGE = "spring-app:1.0"
        FRONTEND_IMAGE = "angular-app:1.0"
    }
 
    stages {
 
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
 
        stage('Build Backend - Spring Boot') {
            steps {
                sh '''
                  cd Spring
                  chmod +x mvnw
                  ./mvnw clean package
                '''
            }
        }
 
        stage('Build Frontend - Angular') {
            steps {
                sh '''
                  cd Angular
                  npm install
                  npm run build
                '''
            }
        }
 
        stage('Build Docker Images') {
            steps {
                sh '''
                  docker build -t $BACKEND_IMAGE Spring
                  docker build -t $FRONTEND_IMAGE Angular
                '''
            }
        }
 
        stage('Deploy Application') {
            steps {
                sh '''
                  docker rm -f spring angular || true
 
                  docker run -d --name spring -p 8081:8080 $BACKEND_IMAGE
                  docker run -d --name angular -p 80:80 $FRONTEND_IMAGE
                '''
            }
        }
    }
 
    post {
        success {
            echo '✅ Spring Boot & Angular deployed successfully'
        }
        failure {
            echo '❌ Pipeline failed'
        }
    }
}
