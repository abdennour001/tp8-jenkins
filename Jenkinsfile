pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle build', returnStatus: true, returnStdout: true, label: 'Hello gradle!')
        powershell(script: 'gradle javadoc', returnStatus: true, returnStdout: true)
      }
    }

  }
}