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
	stage('copy') {
	    steps {
		sh 'apt-get update && apt-get -y install openssh-client'
		sh 'ftp /var/jenkins_home/workspace/demo2/dist root@47.106.85.213:/root/jenkins-data/workspace/githubTest'
	    }
	}
    }
        
}