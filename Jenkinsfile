pipeline {

  agent any
  
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
            sh 'mvn -U -V -e -B -DskipTests deploy -Pdev -DmuleDeploy'
      }
    }
    
  }

 
}
