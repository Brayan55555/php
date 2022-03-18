pipeline {
    agent { docker { image 'php:7.4-apache' } }
    stages {
        stage('build') {
            steps {
                ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'docker build -t hello-php .',
                ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'docker run -p 3000:8081 -d hello-php',
                ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'php --version'
            }
        }
    }
}