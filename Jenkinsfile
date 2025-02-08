pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git url: 'https://github.com/AnushreeSathyan03/ReactApplication.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Linting') {
            steps {
                sh 'npx eslint . --ext .js,.jsx'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Project') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p /var/www/react-app'
                sh 'cp -r build/* /var/www/react-app/'
            }
        }

        stage('Post-Deployment Testing') {
            steps {
                sh 'curl -Is http://localhost | head -n 1'
            }
        }
    }
}
