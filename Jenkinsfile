pipeline{
  agent any
  environment{
	imagename = "dikshant1994/php"
	dockerImage = ''
  }
  stages{
    stage("Cloning Git"){
      steps{
        echo 'Cloning Repo...'
		git([url: 'https://github.com/dikshantSharma1994/php.git', branch: 'master', credentialsId: 'GITHUB_CREDS'])
      }
    }
    stage('Building image') {
		steps{
			script {
				docker.build imagename
			}
		}
	}
	stage('Deploy Image') {
		steps{
			script {
				docker.withRegistry( '', 'DockerHub' ) {
					dockerImage.push("$BUILD_NUMBER")
					dockerImage.push('latest')
				}
			}
		}
	}
}
  post {
        success {
            archiveArtifacts artifacts: '**/*.min.*', onlyIfSuccessful: true
        }
    }
}
