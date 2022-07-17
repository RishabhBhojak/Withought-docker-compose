pipeline {
  agent any
  stage("verify tooling") {
      steps {
        sh '''
          docker version
          docker info
          docker-compose --version 
          curl --version
          
        '''
      }
    }
  
 
    
  stages {
        
    stage('Git') {
      steps {
        git 'https://github.com/RishabhBhojak/nodeappjenkins.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
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
