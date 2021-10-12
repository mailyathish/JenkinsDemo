pipeline {
    agent any

    tools {
        // Install the Maven version configured as maven and add it to the path.
        maven "maven"
    }

    stages {
        stage('checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'master', url: 'https://github.com/mailyathish/JenkinsDemo.git'
                
            }

        }
        
        stage('Execute Maven') {
           steps {
             
                sh 'mvn clean package'             
          }
        }
        
        stage('Execute Maven Verify ') {
           steps {
             
                sh 'mvn clean verify'             
          }
        }
        
        
        stage('Tools Init') {
            steps {
                script {
                sh 'ansible --version'
                sh 'pwd'
                sh 'chmod 400 AWSYathi.pem'
                    
            }
            }
            
        }    
        stage('Ansible Deploy') {
             
            steps {
                script{  
                sh 'ansible-playbook main.yml -i ./inventories/prod/host --private-key=AWSYathi.pem -vv'
            }
        }
        } 
        }
       
     
    }
