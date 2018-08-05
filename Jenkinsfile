pipeline {
    agent any
    stages {
        stage('checkout') { 
            steps {
                git 'https://github.com/cjpcloud/jarrepo.git'

            }
        }
        stage('Build') { 
            steps {
             sh 'mvn clean package'
            }
        }
        stage ('junit') {
            steps {
                
            junit 'target/surefire-reports/*.xml'
}
        }
        stage ( 's3 bucket') {
            steps {
                s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'jenkins369', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-1', showDirectlyInBrowser: false, sourceFile: '**', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'UNSTABLE', profileName: 'bucket', userMetadata: []
            }
        }
       
    }
}
