pipeline {
    agent any
    environment {
        CI          = 'true'
        USER        = credentials('palm-travel-frontend-dev-user')
        SERVER      = credentials('palm-travel-frontend-dev-ip')
    }
    stages {
        stage('Build') {
            steps {
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
        stage('Deploy Staging') {
            when {
                branch 'release*'
            }
            steps {
                echo 'Deploying on staging'
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