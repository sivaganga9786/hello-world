pipeline{
    agent any
    tools{
       maven 'maven'
    }
    stages{
       stage('Mvn Build'){
                steps{
                   sh 'mvn clean package'
                   sh 'mv target/myweb*.war target/myweb.war'
                }
            }
         stage('upload war to nexus'){
                steps{
                   nexusArtifactUploader artifacts: [
                    [artifactId: 'myweb', 
                    classifier: '', 
                    file: 'target/myweb.war', 
                    type: 'war'
                    ]
                    ],
                     credentialsId: 'nexus', 
                     groupId: 'in.javahome', 
                     nexusUrl: '52.206.207.12:8081', 
                     nexusVersion: 'nexus3',
                     protocol: 'http',
                     repository: 'maven-releases', 
                     version: '1.0.0'
                }
            }      
    }
}
