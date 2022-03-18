#!groovy

node {
   // ------------------------------------
   // -- ETAPA: Compilar
   // ------------------------------------
   stage 'Docker'
   
   // -- Descarga código desde SCM
   echo 'Validar version'
   ssh -i ../clave.pem  ubuntu@ec2-54-86-55-166.compute-1.amazonaws.com 'docker-compose --version'
}