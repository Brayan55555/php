pipeline {
    agent { docker { image 'php:7.4-apache' } }
    stages {
        stage('build') {
            steps {
                sh 'docker build -t hello-php .',
                sh 'docker run -p 3000:8081 -d hello-php',
                sh 'php --version'
            }
        }
    }
}