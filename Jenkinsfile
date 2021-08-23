pipeline {

  agent any
  
  environment {
  
    ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
    
  }
  
  
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          bat "mvn test"
      }
    }

  
    
    stage('Deployment') {
      
      steps {
            bat 'mvn -U -V -e -B -DskipTests deploy -Pdev -DmuleDeploy -Danypoint.username="%ANYPOINT_CREDS_USR%" -Danypoint.password="%ANYPOINT_CREDS_PSW%"'
      }
    }
    
  }

 
}