pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
                echo 'test auto scan'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Test'
                sh 'npm run ci'
            }
        }
        stage('Deploy Develop') {
            when {
                branch 'develop'
            }
            steps {
                echo 'Deploying on develop'
            }
        }
        stage('Deploy Master') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying on master'
            }
        }
    }
}