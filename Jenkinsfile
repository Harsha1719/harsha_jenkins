//declarative//
pipeline {
    
    agent any
    
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-harsha')
    }

    stages {

        stage('gitclone') {

            steps {
                git 'https://github.com/Harsha1719/harsha_jenkins.git' 
                
            }
        }

        stage ('Build') {

            steps {
            sh 'docker build -t Harsha1719/harsha_jenkins:latest .' 
            }
        }

        stage('login') {

            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }    
     
        stage('Push') {

            steps {
                sh 'docker push Harsha1719/harsha_jenkins:latest'
            }
        }        
    }

    post {  
        always {
            sh 'docker logout'
        }
    }
}              
