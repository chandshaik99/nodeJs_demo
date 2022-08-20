pipeline {
    agent any
    tools {nodejs install "nodejs 18.5.0" }
    environment {
        NODE_ENV='production'
    }
    
  
    stages {
        stage('source') {
            steps {
               git 'https:/https://github.com/chandshaik99/nodeJs_demo/'
               sh 'cat index.js'
            }
            
        }
        
         stage('build') {
             environment{
                 NODE_ENV='StagingGitTest'
             }
             
            
            steps {
             echo NODE_ENV
             withCredentials([string(credentialsId: 'e8f8ff88-49e0-433a-928d-36a518cd30d6', variable: 'secver')]) {
                // some block
                echo secver
            }
                         sh 'npm install'
            }
            
        }
        
         stage('saveArtifact') {
            steps {
              archiveArtifacts artifacts: '**', followSymlinks: false
            }
            
        }
        
        
        
    }
}
