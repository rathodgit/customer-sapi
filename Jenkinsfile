pipeline {

  agent any
  
  environment {
  
    DEPLOY_CREDS = credentials('ANYPOINT_CREDENTIALS')
    
  }
  
  
  stages {
    stage('Build') {
      steps {
            sh 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          sh "mvn test"
      }
    }

  
    
    stage('Deployment') {
      
      steps {
            sh 'mvn -U -V -e -B -DskipTests deploy -Pdev -DmuleDeploy -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%"'
      }
    }
    
  }

 
}