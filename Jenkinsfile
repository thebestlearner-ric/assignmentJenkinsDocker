pipeline {
  agent any
  stages {
    stage("verify tooling") {
      steps {
        sh '''
          docker version
          docker info
        '''
      }
	}
	stage("docker login"){
		steps {
		  sh '''
		   withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'r1e2a3c4t5z6', usernameVariable: 'learningric')]) 
		   {
			sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
			sh 'docker push learningric/jenkinsdocker:latest'
			} 
		   '''
		  }
		}
	}
}
