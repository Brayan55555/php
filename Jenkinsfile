#!groovy

// node {
//    // ------------------------------------
//    // -- ETAPA: Compilar
//    // ------------------------------------
//    stage 'Docker'
   
//    // -- Descarga código desde SCM
//    echo 'Validar version'
//    sh 'pwd'
//    sh "ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'pwd'"
//    sh "ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'sudo docker build -t hello-php php/.'"
//    sh "ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'sudo docker run -p 8081:80 -d hello-php'"
// }


pipeline {
    agent any
    stages {
        stage('checkout from gitlab') {
            steps {
                git branch: 'master',
		        credentialsId: 'gitab-darboleda',
		        url: 'https://github.com/Brayan55555/php.git'
            }
        }
        
        stage('Code Quality'){
            steps {
                script {
                    def scannerHome = tool 'sonarqube';  //global tool configuration http://172.17.0.1:8080/configureTools/
        			   withSonarQubeEnv("Sonarqube-container") { //sonarqube server http://172.17.0.1:8080/configure
        			   sh "${tool("sonarqube")}/bin/sonar-scanner \
        							-Dsonar.projectKey=lumen-ci \
                                    -Dsonar.sources=. \
                                    -Dsonar.language=php \
									-Dsonar.exclusions=vendor \
                                    -Dsonar.sourceEncoding=UTF-8 \
                                    -Dsonar.host.url=http://ip172-18-0-115-c8svmsnnjsv000cnm3jg-9500.direct.labs.play-with-docker.com \
                                    -Dsonar.login=2112e9174263d0867f3af83d5aa7498db7b22a08"
        				   }
                }
            }
        }
    }
}
