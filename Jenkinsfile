pipeline {
    agent any // window agent, Jenkins-laravel (other machine)
    environment {
        BOT_TOKEN = "6934255676:AAHf2Rm0wB9T72z9xKits2FMsLVq87_3ag0"
        CHAT_ID = "-1002082381882"
    }
    stages {
        stage('Fetch from GitHub') { //build steps
            steps {
                echo 'Fetching for GitHub'
                git branch: 'vuejenkin', url: 'https://github.com/Unsengly/devops_jenkins.git'
            }
        }
        stage('Build using Tools'){
            steps{
                echo 'Compiling code ...'
                sh 'npm install'
            }
        }
        stage('Test the app'){
            steps{
                echo 'Testing unit tests...'
                echo 'Testing feature...'
                sh 'npm run build'
            }
        }
        
    }
    post{
            success{
                sh '''
                sh success-deploy.sh;\
                '''
            }
            failure{
                sh '''
                sh fail-deploy.sh;\
                '''
            }
    }
}