pipeline {
  agent any
     
  //tools {nodejs "node"}
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/rafaelquintella/test'
      }
    }
             
    stage('Test') {
      steps {
         sh 'echo oi'
      }
    }      
  }
}