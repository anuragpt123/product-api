pipeline {

  agent any

  tools{
    mavem 'M3'
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

    stage('Deploy Development') {

      steps {
        sh 'mvn -U -V -e -B -DskipTests -Ptest deploy -DmuleDeploy'
      }
    }
  }
}
