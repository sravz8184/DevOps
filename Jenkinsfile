pipeline {
    agent any
    
   tools{
        maven 'M2_HOME'
    }
    
    stages{
        
        stage("checkout") {
          steps{
           checkout([$class: 'GitSCM', branches: [[name: '*/test']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sravz8184/DevopsBasics.git']]]) 
            }
          }
        stage("build") {
            steps{
                sh 'mvn clean package'
            }
        }
        stage("upload to S3") {
            steps{
                s3Upload consoleLogLevel: 'INFO', dontSetBuildResultOnFailure: false, dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 's3-artifact-upload', excludedFile: '/webapp/target', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'ap-south-1', showDirectlyInBrowser: false, sourceFile: '**/webapp/target/*.war', storageClass: 'STANDARD', uploadFromSlave: true, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'S3-Artifact-Demo', userMetadata: []
            }
        }
    }
}
