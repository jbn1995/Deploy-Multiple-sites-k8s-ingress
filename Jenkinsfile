pipeline {
    agent any
    
    stages {
        stage('Pull code from GitHub') {
            steps {
                checkout([$class: 'GitSCM', 
                          branches: [[name: 'main']], 
                          userRemoteConfigs: [[url: 'https://github.com/jbn1995/multis-site-k8s-ingress-project.git']]
                ])
            }
        }
       
        stage('Deploy images to Kubernetes') {
            steps {
                script {
                    // Point kubectl to Minikube's context
                    sh 'kubectl config use-context minikube'
                    sh 'kubectl apply -f website1-deployment_service.yml'
                    sh 'kubectl apply -f website2-deployment_service.yml'

                    // Deploy ingress resources files
                    sh 'kubectl apply -f host-base-routing-ingrs/ingress.yml'
                    sh 'kubectl apply -f path-based-routing-ingrs_website1/ingress_path_tls.yml'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment completed successfully! '
        }
        failure {
            echo 'Build or deployment failed.'
            
        }
        always {
            echo 'Clean Up the workspace.'
            cleanWs()  // Cleans up the workspace
        }
    }
}

