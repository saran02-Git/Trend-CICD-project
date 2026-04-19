pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "saran0702/trend-app:v2"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE ./app'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh '''
                  kubectl apply -f k8s/deployment.yaml
                  kubectl apply -f k8s/service.yaml
                  kubectl get pods
                  kubectl get svc
                '''
            }
        }
    }

    post {
        success {
            echo "SUCCESS Build, Push & Deploy completed"
        }
        failure {
            echo "FAILED  Check Jenkins console logs"
        }
    }
}
