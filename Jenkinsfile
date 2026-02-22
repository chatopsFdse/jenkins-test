pipeline {
    agent any

    options {
        // Keep build logs for some time, adjust as needed
        buildDiscarder(logRotator(numToKeepStr: '20'))
        timestamps()
    }

    triggers {
        // Optional: build on every push to main
        // pollSCM('* * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout main branch from GitHub
                git(
                    url: 'https://github.com/chatopsFdse/jenkins-test',
                    branch: 'main'
                )
            }
        }

        stage('List files') {
            steps {
                sh 'pwd && ls -R'
            }
        }
    }

    post {
        success {
            echo 'Checkout from main branch completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
