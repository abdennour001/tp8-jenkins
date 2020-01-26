pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle build', label: 'Hello gradle!')
        powershell 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle javadoc'
        archiveArtifacts 'build/libs/**/*.jar'
        archiveArtifacts 'build/reports/**'
        junit 'build/test-results/test/*.xml'
      }
    }

    stage('Mail Notification') {
      steps {
        mail(subject: 'Notification', body: 'Notification', cc: 'fa_amokrane@esi.dz', to: 'fa_amokrane@esi.dz')
      }
    }

  }
}