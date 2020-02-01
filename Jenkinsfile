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
        mail(subject: 'Notification', body: 'Notification', to: 'fa_amokrane@esi.dz')
      }
    }

    stage('Code Analysis') {
      parallel {
        stage('Code Analysis') {
          steps {
            withSonarQubeEnv('sonar') {
              bat 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle sonarqube'
            }

            waitForQualityGate true
          }
        }

        stage('Test Reporting') {
          steps {
            jacoco()
          }
        }

      }
    }
  }
}
