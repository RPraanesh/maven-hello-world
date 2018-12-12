pipeline {
    agent any
    stages {
        stage('CodeCheckOut') {
            steps {
                script {
                    checkout scm
                    def mvnHome = tool 'maven'
                }
            }
        }
		
		
        stage('Build Customer app code') {
            steps {
                script {
                   
                    checkout scm
                    def mvnHome = tool 'maven'
                    try {
                        sh "${mvnHome}/apache-maven-3.5.0/bin/mvn clean install -U -Dmaven.test.skip=true"
                        currentBuild.result = 'SUCCESS'
                    } catch (Exception err) {
                        currentBuild.result = 'FAILURE'
                        sh "exit 1"
                    }
                    
                }
            }
       }
    }}
		
