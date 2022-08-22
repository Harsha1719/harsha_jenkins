//declarative//
pipeline {
    
    agent any
    
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-harsha')
    }

    stages {

        stage('gitclone') {

            steps {
		git branch: 'main', url: 'https://github.com/Harsha1719/harsha_jenkins.git'
              
                
            }
        }

        stage ('Build') {

            steps {
            sh 'sudo docker build . -t node_harsha:latest' 
            }
        }

        stage('login') {

            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }    
     
        stage('Push') {

            steps {
                sh 'sudo docker push node_harsha:latest'
            }
        }        
    }

    post {  
        always {
            sh 'docker logout'
        }
    }
}              
