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
            sh 'zip -r ./* --exclude=.git --exclude=.zip'
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