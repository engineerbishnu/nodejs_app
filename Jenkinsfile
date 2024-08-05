pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'engineer442/nodejs-helloworld:latest'
        KUBE_NAMESPACE = 'default' // Adjust as needed
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    kubernetesDeploy(
                        configs: 'node-app-with-service.yaml',
                        kubeconfigId: 'kubeconfig-credentials'
                    )
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}
