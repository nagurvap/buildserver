pipeline {
  agent any
  stages {
    stage('Review') {
      steps {
        powershell 'init/lint.ps1'
        powershell 'init/unit.ps1'
        input(message: 'Do you approve changes?', id: 'init_approve_id', ok: 'Yes')
      }
    }
    stage('Build') {
      steps {
        powershell 'build/lint.ps1'
        powershell 'build/unit.ps1'
        powershell 'build/create.ps1'
        powershell 'build/provision.ps1'
        powershell 'build/smoke.ps1'
      }
    }
    stage('Test') {
      steps {
        powershell 'test/test.ps1'
        input(message: 'Do you certify the environment', id: 'test_approve_id', ok: 'Yes')
      }
    }
    stage('Deliver') {
      steps {
        powershell 'deliver/provision.ps1'
        powershell 'deliver/status.ps1'
      }
    }
  }
}