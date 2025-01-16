pipeline {
    agent any

    environment {
        KUBECONFIG = '/var/lib/jenkins/.kube/config'  // This is where we copied the config
    }

    triggers {
        pollSCM('* * * * *')  // Polls the repo every minute (Webhooks are preferred)
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
                    sh 'helm upgrade --install my-webapp ./ --namespace default'
                }
            }
        }
    }
}

