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
    post { 
        always { 
            echo 'Build result'
        }
        success {
            echo 'build success'
            // slackSend channel: '#devops',
            //       color: 'good',
            //       message: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
            // mail to: 'thada.p@blockfint.com',
            //     subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
            //     body: "Something is wrong with ${env.BUILD_URL}"
        }
        failure {
            echo 'Build failed'
        }
        aborted {
            echo 'Build abort'
        }
    }
}