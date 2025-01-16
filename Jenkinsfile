pipeline {
    agent any

    environment {
        KUBECONFIG = '/home/ubuntu/.kube/config'  // Ensure Jenkins uses the correct config file
    }

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/TejiriH/Helm-learn-Jenkins'
            }
        }

        stage('Deploy with Helm') {
            steps {
                script {
                    sh 'export KUBECONFIG=/home/ubuntu/.kube/config && helm upgrade --install my-webapp ./ --namespace default'
                }
            }
        }
    }
}

