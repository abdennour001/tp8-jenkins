pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle build', label: 'Hello gradle!')
        powershell(script: 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle javadoc', returnStatus: true, returnStdout: true)
      }
    }

  }
}