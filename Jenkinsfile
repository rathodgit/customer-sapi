pipeline {

  agent any
  
  environment {
  
    DEPLOY_CREDS = credentials('Mule_CREDS')
    
  }
  
  
  stages {
    stage('Build') {
      steps {
            sh 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          echo "***** Munit test disabled *****"
      }
    }

  
    
    stage('Deployment') {
      
      steps {
            sh 'mvn -U -V -e -B -DskipTests deploy -Pdev -DmuleDeploy -Dusername="%DEPLOY_CREDS_USR%" -Dpassword="%DEPLOY_CREDS_PSW%"'

      }
    }
    
  }

 
}
