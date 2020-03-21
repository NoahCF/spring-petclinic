pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './mvnw clean' 
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test' 
            }
        }
        stage('Package') {
            steps {
                sh './mvnw package' 
            }
        }
       stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                sh './mvnw deploy'
            }
        }
    }
    post {
    success {
        slackSend message: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
            }
    }   
}
