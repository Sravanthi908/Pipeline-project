pipeline {
    agent any
    
    stages {
        // Stage 1: Build & Check
        stage('1. Build & Check') {
            steps {
                echo 'Running build and packaging...'
                sh 'mvn clean package'
            }
        }
        
        // Stage 2: Docker Build & Push
        stage('2. Docker Build & Push') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t sravanthi908/hello-service:latest .'
                
                // Uncomment the line below once you have logged into Docker / configured credentials in Jenkins
                // sh 'docker push sravanthi908/hello-service:latest'
            }
        }
        
        // Stage 3: Kubernetes Deployment
        stage('3. K8s Deploy') {
            steps {
                echo 'Applying Kubernetes deployment and service manifests...'
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
                sh 'kubectl rollout status deployment/hello-service-deployment'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}