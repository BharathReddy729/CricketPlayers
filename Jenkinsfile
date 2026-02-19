pipeline {
    agent any
 
    environment {
        BACKEND_IMAGE = "spring-app:${BUILD_NUMBER}"
        FRONTEND_IMAGE = "angular-app:${BUILD_NUMBER}"
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
                  ./mvnw clean package -DskipTests
                '''
            }
        }
 
        stage('Build Frontend - Angular') {
            steps {
                sh '''
                  cd Angular
                  npm ci
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
        stage('Security scan-TRIVY') {
            steps {
                sh '''
                  trivy image --severity HIGH,CRITICAL --exit-code 1 $FRONTEND_IMAGE
                  trivy image --severity HIGH,CRITICAL --exit-code 0 $BACKEND_IMAGE
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
