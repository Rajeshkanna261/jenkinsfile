pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from Rajeshkanna261/jenkinsfile...'

                git branch: 'main',
                    url: 'https://github.com/Rajeshkanna261/jenkinsfile.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building website...'

                sh 'ls -la'
                sh 'test -f index.html'

                echo 'Build completed successfully.'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing website...'

                sh 'test -s index.html'

                echo 'Test passed successfully.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website to Nginx...'

                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp index.html /var/www/html/index.html
                '''

                echo 'Deployment completed successfully.'
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying deployment...'

                sh '''
                    test -f /var/www/html/index.html
                    curl -f http://localhost
                '''

                echo 'Website verification successful.'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed. Check the Console Output.'
        }
    }
}
