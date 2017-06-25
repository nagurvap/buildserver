pipeline {
  agent any
  stages {
    stage('Review') {
      steps {
        input(message: 'Do you approve the changes?', id: 'sql_ec2_approve', ok: 'yes')
      }
    }
  }
}