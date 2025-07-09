pipeline{
    
agent any

stages{
    stage('Clone The Project'){
        steps{
            git branch: 'release/2025.07.19', url: 'git@github.com:srinfotechbatch2/devOpsWeb.git'
        }
    }
    
    stage('Build'){
        steps{
             bat 'mvn clean install'
        }
    }
     stage('Test'){
        steps{
             bat 'mvn test'
        }
    }
  
     stage('published the Artifacts'){
        steps{
            archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
        }
    }
    
    stage('Deploy to Tomcat Server'){
        steps{
            deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcatcredential', path: '', url: 'http://localhost:8080')], contextPath: 'SRInfotechWebApplication', war: 'target/*.war'
        }
    }
}
}