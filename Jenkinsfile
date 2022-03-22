
pipeline {
    agent any
    stages {
        stage('checkout from gitlab') {
            steps {
                git branch: 'master',
		        credentialsId: 'php',
		        url: 'https://github.com/Brayan55555/php.git'
            }
        }
        
        stage('Code Quality'){
            steps {
                script {
                    def scannerHome = tool 'sonarqube';  //global tool configuration http://172.17.0.1:8080/configureTools/
        			   withSonarQubeEnv("sonarqube-container") { //sonarqube server http://172.17.0.1:8080/configure
        			   sh "${tool("sonarqube")}/bin/sonar-scanner \
        							-Dsonar.projectKey=php \
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
