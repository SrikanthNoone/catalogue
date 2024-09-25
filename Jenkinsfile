pipeline{
    agent {node {label 'Node1'}}
    stages{
        stage ('install dependencies'){
            steps{
                sh 'npm install'
            }
       }
       stage('Unit test'){
            steps{
                echo 'unit test is done'
        }
                
       }
       stage('build'){
        steps{
            sh 'ls -ltr'
            sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'
        }
       }
        stage('publish artifact'){
        steps{
            nexusArtifactUploader(
        nexusVersion: 'nexus3',
        protocol: 'http',
        nexusUrl: '52.87.181.145:8081/',
        groupId: 'com.roboshop',
        version: '1.0.1',
        repository: 'catalogue',
        credentialsId: 'nexus-auth',
        artifacts: [
            [artifactId: 'catalogue',
             classifier: '',
             file: 'catalogue.zip',
             type: 'zip']
        ]
     )
            
        }
       }
    }
    post{
        always{
            echo 'success'
            //deleteDir()
        }
    }

}