pipeline {
  agent any
     
  //tools {nodejs "node"}
    
  stages {
    //Atualiza o código da aplicação
    stage('Update') {
      steps {
         sh 'ssh $SSH_USER@$SSH_HOST    cd simple-chat && git pull origin main --force'
      }
    }   
    stage('Configure') {
      steps {
         sh 'ssh $SSH_USER@$SSH_HOST    sed -i "s/URL_DATABASE/teste/g" server.js'
      }
    }  
    //Build a imagem
    stage('Build') {
      steps {
         sh 'ssh $SSH_USER@$SSH_HOST	docker build -t simple-chat:latest simple-chat/'
      }
    } 
    //Deploy
    stage('Deploy') {
      steps {
         sh 'ssh $SSH_USER@$SSH_HOST	docker container rm -f app-node || true'
         sh 'ssh $SSH_USER@$SSH_HOST	docker container run -d -p 8000:3000 --name app-node simple-chat:latest'
      }
    } 

  }
}