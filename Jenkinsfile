pipeline {
    agent any

    stages {
        stage('Begin') {
            steps {
              echo 'Begin..'
              build_log() {
                echo $1 >> $2.log
                echo '\n' >> $2.log
              }
              rm -f sdlc_management_build.log
              build_log 'Building sdlc_management_build' sdlc_management_build
              build_log "Running from folder $(pwd)" sdlc_management_build
              build_log "Containaing Environment Variable $(env)" sdlc_management_build
              build_log "Running from agent $(hostname)" sdlc_management_build
            }
        }
        stage('Download') {
            steps {
              echo 'Download..'
            }
        }
        stage('Verify') {
            steps {
              echo 'Verify..'
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
