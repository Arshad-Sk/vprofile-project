pipeline {
    agent any
    tools {
       maven 'maven3'
    }
   
    stages {
            stage('Build')
            {
               steps {
                    sh script: "mvn clean package"
                    sh "echo \$PWD"
                    sh "whoami"
                  }
            }
            
            stage('Upload war to nexus')
            {
                steps {
                       nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'vprofile', 
                            classifier: '',
                            file: 'target/Visualpathit VProfile Webapp-v1', 
                            type: 'war'
                        ]
                        ], 
                        credentialsId: 'nexus3', 
                        groupId: 'com.visualpathit', 
                        nexusUrl: '172.31.31.100', 
                        nexusVersion: 'nexus3', 
                        protocol: 'http', 
                        repository: 'http://3.23.94.253:8081/repository/vpro-release/', 
                        version: 'v1'                    }
            }
    
    }
}
