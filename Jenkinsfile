pipeline{
  agent{
    node{
      label 'docker'
    }
  }
  stages{
    stage('verify tools'){
     steps{
       sh '''
        docker info
        docker version
        docker-compose version
       '''
     }  
    }
    stage('sq-scanner'){
      steps{
        script{
          withSonarQubeEnv('SDPM_Sonarqube') {
          
            // Execute SonarQube scanner
            def scannerHome = tool 'SonarQube_Scanner'
            sh "${scannerHome}/bin/sonar-scanner"

          }
        }
      }
    }
   }
}
