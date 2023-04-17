pipeline {
	agent any
	stages {
		stage('Clone git') {
			steps{
				git branch: 'master', url: 'https://github.com/thuongnv00/demo-jenkin-java.git'
			}
		}
		stage('Docker build and push') {
			steps{
				sshagent (credentials: ['ssh-remote']) {
               			sh 'ssh -o StrictHostKeyChecking=no -l vsii 192.168.0.221 docker build -t kenshinthuong/springboot-demo:v1 .'
				sh 'ssh -o StrictHostKeyChecking=no -l vsii 192.168.0.221 docker push kenshinthuong/springboot-demo:v1'
                		}
			}
		}

		
	
	}
}
