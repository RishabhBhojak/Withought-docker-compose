pipeline {
  agent any
  
  
 
    
  stages {
        
    stage('Git') {
      steps {
        git 'https://github.com/RishabhBhojak/nodeappjenkins.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm init'
        sh ' docker build -t rishabhbhojak/mynodeimg .' 
      }
    }  
    
            
    stage('Test') {
      steps {
        sh 'node test'
      }
    }
  }
}
