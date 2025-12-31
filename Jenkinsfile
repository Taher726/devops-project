pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Taher726/devops-project.git'
            }
        }

        stage('Validate HTML & CSS') {
            steps {
                sh 'echo Validating HTML...'
                sh 'tidy -qe index.html'
                sh 'echo Validatin CSS...'
                sh 'csslint style.css || echo CSS validation warnings'
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r * /var/www/html/
                    sudo service apache2 restart
                '''
            }
        }
    }

    post {
        success {
            echo "Deployment Successful 🚀"
        }
        failure {
            echo "Deployment Failed ❌"
        }
    }
}
