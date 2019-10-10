pipeline {   
  agent {
    node {
      label 'master'
    }  
  }
  stages {
    stage('Initialize') {
      steps {
        sh 'echo Hello User, You are about to create GCP IaaS resources'
      }
    }
    stage ('Approval to Provision') { 
      options {
        timeout (time: 1, unit: 'HOURS')
      } 
      steps {
        input 'Approve The Plan To Proceed And Apply'
      }
    } 
}
}
