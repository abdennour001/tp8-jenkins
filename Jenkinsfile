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

          }
        }

        stage('Test Reporting') {
          steps {
            jacoco()
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        bat 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle uploadArchives'
      }
    }

    stage('Slack Notification') {
      steps {
        slackSend(message: 'The project was successfully deployed.', attachments: 'Hello', blocks: 'Hello', baseUrl: 'https://hooks.slack.com/services/', channel: '#lol', token: 'TTD9T1DGE/BTCV3KL2K/Y1btG6VbekQdvKnalthpAt1J', teamDomain: 'esi-53p7429')
      }
    }

  }
}