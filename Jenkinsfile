pipeline {
    agent any
    
   tools{
        maven 'M2_HOME'
    }
    
    stages{
        
        stage("checkout") {
          steps{
           checkout([$class: 'GitSCM', branches: [[name: '*/Test']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sravz8184/DevopsBasics.git']]]) 
            }
          }
    }
}
