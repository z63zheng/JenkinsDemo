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
	    def remote = [:]
    	    remote.name = '47.106.85.213'
            remote.host = '47.106.85.213'
            remote.user = 'root'
            remote.allowAnyHosts = true
            stage('Remote SSH') {
                sshPut remote: remote, from: '/var/jenkins_home/workspace/demo2/dist', into: '/root/jenkins-data/workspace/githubTest'
    	    }
	}
    }
        
}