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
				withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
				sh 'docker build -t kenshinthuong/springboot-demo:v1 .'
				sh 'docker push kenshinthuong/springboot-demo:v1'
				
				}
			}
		}
		stage('Run container in Kubernetes') {
			steps{
				echo 'Kubernetes ...............................'
				script {
					kubernetesDeploy(configs: "deployment.yml",kubeconfigId:"kubernetes")
				}
			}
		}
		
	
	}
}
