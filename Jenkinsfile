pipeline {
    agent {
        docker {
            image 'node:9-alpine' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('install') { 
            steps {
                sh 'npm install --registry=https://registry.npm.taobao.org' 
            }
        }
        stage('build') { 
            steps {
                sh 'npm run build' 
            }
        }
    }    
}