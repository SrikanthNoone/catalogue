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
        nexusUrl: '44.202.36.115:8081/',
        groupId: 'com.roboshop',
        version: '1.0.0',
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
            deleteDir()
        }
    }

}