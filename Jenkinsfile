pipeline {
  agent any
     
  //tools {nodejs "node"}
    
  stages {
    //Clone do repositório                 
    stage('Clone') {
      steps {
         sh 'ssh $SSH_USER@SSH_HOST	git clone https://github.com/rafaelquintella/simple-chat || true'
      }
    }  
    //Atualiza o código da aplicação
    stage('Update') {
      steps {
         sh 'ssh $SSH_USER@SSH_HOST	cd simple-chat && git pull origin main'
      }
    }   
    //Build a imagem
    stage('Build') {
      steps {
         sh 'ssh $SSH_USER@SSH_HOST	docker build -t simple-chat simple-chat/'
      }
    } 
    //Deploy
    stage('Deploy') {
      steps {
         sh 'ssh $SSH_USER@SSH_HOST	docker container rm -f app-node || true'
         sh 'ssh $SSH_USER@SSH_HOST	docker container run -d -p 8000:3000 --name app-node simple-chat'
      }
    } 

  }
}