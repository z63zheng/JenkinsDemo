pipeline {
    node {
    stages {
	stage('build') {
	    agent {
                docker {
            	    image 'node:9-alpine' 
            	    args '-p 3000:3000'
        	}
    	    }
	    steps {
		sh 'npm install --registry=https://registry.npm.taobao.org' 
		sh 'npm run build' 
	    }
	}
	stage('copy') {
	    steps {
		sh 'scp -r /var/jenkins_home/workspace/demo2/dist root@47.106.85.213:/root/jenkins-data/workspace/githubTest'
	    }
	}
    }
    }
        
}