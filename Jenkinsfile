pipeline {
    agent any
    stages {
        stage('Clone Helm Chart') {
            steps {
                git 'https://github.com/rishi97/test-app.git'   
            }
        }
        stage('Build Helm Chart') {
            steps {
                sh 'helm lint test-app/helm-example/'
            }
        }
        stage('Deploy Helm Chart') {
            steps {
                // sh 'kubectl --namespace your-namespace create secret tls your-secret-name --cert=path/to/tls.crt --key=path/to/tls.key'
                sh 'kubectl --namespace test-ns'
                sh 'helm upgrade --install test-app test-app/helm-example/ --namespace test-ns'
                // sh 'helm upgrade --install test-app helm-example/ --namespace test-ns --set image.tag=${BUILD_NUMBER} --set ingress.tls[0].secretName=your-secret-name'
            }
        }
    }
}
