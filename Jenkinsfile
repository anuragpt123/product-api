pipeline {

  agent any
  
  envirnment{
   ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
   
  }
  tools {
    maven 'M3'
    jdk 'java17'
  }

stages {
    stage('Build') {
      steps {
        sh 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
       echo " ******** Mule test cases execution mocked "
      }
    }

    stage('Development') {
    
    environment{
     CLIENT_ID = credentials('DEV_CLIENT_ID')
     CLIENT_SECRET = credentials('DEV_CLIENT_SECRET')
    }

      steps {
        sh 'mvn -U -V -e -B -DskipTests -Ptest deploy -DmuleDeploy -Danypoint.username="%ANYPOINT_CREDS_USR%" -Danypoint.password="%ANYPOINT_CREDS-PSW%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%"'
      }
    }
  }
}