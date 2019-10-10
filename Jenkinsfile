pipeline {   
  agent {
    node {
      label 'master'
    }  
  }
  stages {
    stage('Initialize') {
      steps {
        sh 'echo Hello Solution Arch, You are About To Create GCP IaaS Resources Using Deployment Manager Template'
      }
    }
    //stage ('Approval to Provision') { 
    // options {
    //    timeout (time: 1, unit: 'HOURS')
    //  } 
    //  steps {
    //    input 'Approve The Plan To Proceed And Apply'
    //  }
    //} 
    stage ('Create') {
           steps {
           sh 'cd examples/v2/step_by_step_guide/step6_use_multiple_templates/python && gcloud deployment-manager deployments create provisioning-gcp \
  --config config-with-many-templates.yaml'
           }
    }
    stage ('Approval to De-Provision') {
      options {
         timeout (time:1, unit: 'HOURS')
      }
      steps {
        input 'Approve to Proceed And Apply'
      }
    }
    stage ('Destroying The GCP Resources with Deployment-Name') {
      steps { 
         sh 'gcloud deployment-manager deployments delete provisioning-gcp'
      }
    }
}
}
