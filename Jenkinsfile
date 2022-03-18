#!groovy

node {
   // ------------------------------------
   // -- ETAPA: Compilar
   // ------------------------------------
   stage 'Docker'
   
   // -- Descarga código desde SCM
   echo 'Validar version'
   sh 'pwd'
   sh "ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'pwd'"
   sh "ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'sudo docker build -t hello-php php/.'"
   sh "ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'sudo docker run -p 3000:8081 -d hello-php'"
}