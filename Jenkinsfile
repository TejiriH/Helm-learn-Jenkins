pipeline {
    agent any

    environment {
        KUBECONFIG = '/home/ubuntu/.kube/config'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/TejiriH/Helm-learn-Jenkins'
            }
        }

        stage('Check File Permissions') {
            steps {
                script {
                    sh 'ls -l /home/ubuntu/.kube/config'
                    sh 'ls -l /home/ubuntu/.minikube/profiles/minikube/*'
                }
            }
        }

        stage('Deploy with Helm') {
            steps {
                script {
                    sh '''
                        export KUBECONFIG=/home/ubuntu/.kube/config
                        helm upgrade --install my-webapp ./ --namespace default
                    '''
                }
            }
        }
    }
}

