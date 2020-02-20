pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        echo 'Running build automation'
        sh './gradlew build --no-daemon'
        archiveArtifacts artifacts: 'dist/trainSchedule.zip'
      }
    }
    stage ('Deploy') {
        steps {
            sshPublisher(publishers: [sshPublisherDesc(configName: 'prod', sshCredentials: [encryptedPassphrase: '{AQAAABAAAAAQcDkDDF31woL+pX7A9I7pa+AKcUOmpaOvbp0iFoAfVLI=}', key: '', keyPath: '', username: 'deploy'], transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/opt/train-schedule', remoteDirectorySDF: false, removePrefix: '/dist', sourceFiles: '/dist/trainSchedule.zip')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        }
    }
    }
  }
