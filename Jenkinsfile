pipeline {
  agent any
  environment {
        DOCKERHUB_CREDENTIALS_PSW="f1d00111-ecbc-48ed-b5cf-8d99e2a9e5d4"
        DOCKERHUB_CREDENTIALS_USR="rishabhbhojak" 
        
  }      
  stages {
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
    stage('Prune Docker data') {
      steps {
        sh 'docker system prune -a --volumes -f'
      }
    }
    
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t rishabhbhojak/dockerfilenode:latest .'
      }
    }

     
    stage('login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }

    stage('push images') {
      steps {
        sh 'docker push rishabhbhojak/dockerfilenode:latest'
      }
    }
//     stage('Run tests against the container') {
//       steps {
//         sh 'curl http://localhost:3000/param?query=demo | jq'
//       }
//     }
  }
//   post {
//     always {
// //       sh 'docker-compose down'
// //       sh 'docker compose ps'
//     }
//   }
}
