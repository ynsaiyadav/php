pipeline{
  agent any
  stages{
    stage("build"){
      steps{
        echo 'Building the application...'
      }
    }
  }
  post {
        always {
            archiveArtifacts artifacts: '**/*.min.*', onlyIfSuccessful: true
        }
    }
}
