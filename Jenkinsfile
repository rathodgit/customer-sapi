pipeline {

  agent any
  
  environment {
  
    ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
    
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
            sh 'mvn -U -V -e -B -DskipTests deploy -Pdev -DmuleDeploy -Dusername="%ANYPOINT_CREDS_USR%" -Dpassword="%ANYPOINT_CREDS_PSW%"'
      }
    }
    
  }

 
}
