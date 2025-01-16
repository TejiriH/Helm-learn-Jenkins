pipeline {
    agent any

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
                    sh '/usr/local/bin/helm upgrade --install my-webapp ./webapp --namespace default'
                }
            }
        }
    }
}

