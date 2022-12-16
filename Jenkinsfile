pipeline {
    agent any
    
    stages {
        stage('Git-Checkout') {
            steps{
                echo 'Checking out Git repo'
	            git branch: 'main', url: 'https://github.com/Krreesh/-public-pipeline.git'
            }
        }
        stage('Build') {
            steps{
                sh './build.sh'
            }
        }
	stage('Unit-Test'){
	    steps{
		sh './unit.sh'
	  }
	}
        stage('Quality-Gate'){
            steps{
                sh './quality.sh'
            }
        }
        stage('Deploy'){
            steps{
                sh './deploy.sh'
            }
        }
    }
    post {
        always {
            echo "Runs always"
        }
        success {
            echo "Runs only successful"
        }
        failure {
            echo "Runs when failed"
        }
        unstable {
            echo "Runs when run marked unstable"
        }
        changed {
            echo "Runs only when state of pipepline changed"
        }
    }
}
