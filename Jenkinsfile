pipeline {

    agent any 
        tools {
            maven 'maven'
        }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                
                echo "Cleaned Up Workspace For Project"
                
            }
        }

        stage('Code Checkout') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/etechDevops/multibranch-build.git']]])
            }
        }

        stage(' Unit Testing') {
            steps {
                
                echo "Running Unit Tests"
                sh 'mvn test'

            }
        }

        stage('Code Analysis') {
            steps {
                
                echo "Running Code Analysis"
                
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                
                echo "Building Artifact"
                         
                echo "Deploying Code"
               
            }
        }

    }   
}
