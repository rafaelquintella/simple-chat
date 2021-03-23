pipeline {
  agent any

  stages {
        
    stage('Cloning Git') {
      steps {
        sh 'ssh $SSH_USER@SSH_HOST	git clone https://github.com/rafaelquintella/simple-chat || true'
    }
        
    // stage('Install dependencies') {
    //   steps {
    //     sh 'npm install'
    //   }
    // }
     
    // stage('Test') {
    //   steps {
    //      sh 'echo oi'
    //   }
    // }      
  }
}