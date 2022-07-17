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
        
        sh ' docker build -t rishabhbhojak/mynodeimg .' 
      }
    }  
    
            
   
  }
}
