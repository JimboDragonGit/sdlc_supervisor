pipeline {
  agent any

  stages {
    stage('Begin') {
      steps {
        echo 'Begin..'
      }
    }
    stage('Download') {
      steps {
        wrap([$class: 'TimestamperBuildWrapper']) {
          echo 'Download..'
        }
      }
    }
    stage('Verify') {
      steps {
        wrap([$class: 'TimestamperBuildWrapper']) {
          tool name: 'Default', type: 'git'
          echo 'Verify..'
          }
        }
      }
    }
    stage('Clean') {
      steps {
        echo 'Clean..'
      }
    }
    stage('Unpack') {
      steps {
        echo 'Unpack..'
      }
    }
    stage('Prepare') {
      steps {
        echo 'Prepare..'
      }
    }
    stage('Build') {
      steps {
          echo 'Building..'
      }
    }
    stage('Check') {
      steps {
        echo 'Check..'
      }
    }
    stage('Install') {
      steps {
        echo 'Install..'
      }
    }
    stage('Strip') {
      steps {
        echo 'Strip..'
      }
    }
    stage('End') {
      steps {
        echo 'Finishing..'
      }
    }
  }
}
