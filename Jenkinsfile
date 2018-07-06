pipeline {
    agent {
        docker {
            image 'node:9-alpine' 
            args '-p 3000:3000' 
        }
    }
    agent {
	docker {
	    image 'openssh-server'
	    args '-y'
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
		sh 'scp -r /var/jenkins_home/workspace/demo2@tmp/dist root@47.106.85.213:/root/jenkins-data/workspace/githubTest'
	    }
	}
    }
        
}