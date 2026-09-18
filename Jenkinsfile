@Library('sharedlib') _
pipeline {
environment{
    registry ='himanshurana08/bravopro'
    registryCredential ='dockerhubId'
   dockerimg =''
}

    agent {label 'bravo'}

    stages {
        stage('Greeting') {
            steps {
                script{
                        hello()
                }
            }
        }
        
        stage('Clone'){
            steps{
                echo "This is clone Phase"
                git url:'https://github.com/HimanshuRana08/django-notes-app.git', branch :'main'
                echo "The cloning is successfull"
            }
        }
        stage('Build'){
            steps{
                echo 'This is build phase'
                script{
                dockerimg=docker.build ("${registry}:notesapp-version1-$BUILD_NUMBER")
            }
        }
    }    
        stage('push'){
            steps{
            script{
                docker.withRegistry('',registryCredential){
                    
                    dockerimg.push()
                }
            }
            
        
        }        
            }
    }
}
