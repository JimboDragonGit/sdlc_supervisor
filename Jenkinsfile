pipeline {
  agent { label 'prod' }

  environment {
    PATH = '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:/opt/chef-workstation/bin:/opt/chef-workstation/embedded/bin/:/root/.chef/gem/ruby/3.1.0/bin/'
  }

  parameters {
    string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    string(name: 'generator', defaultValue: '/chef/cookbooks/code_generator', description: 'code generator path')
    string(name: 'chefrepo', defaultValue: 'default', description: 'chef')
  }

  stages {
    stage('Begin') {
        steps {
          wrap([$class: 'TimestamperBuildWrapper']) {
            echo 'Begin..'
            echo "${params.Greeting} World!"
            sh 'knife config show'
            sh 'chef show-policy builder_unix'
            sh 'chef show-policy builder_windows'
            sh 'chef-client -o sdlc_structure::begin'
          }
        }
    }
    stage('Download') {
      steps {
        wrap([$class: 'TimestamperBuildWrapper']) {
          echo 'Download..'
            sh "su -c 'save_databag' jimmy.provencher"
            sh 'chef-client -o sdlc_structure::download'
        }
      }
    }
    stage('Verify') {
      steps {
        wrap([$class: 'TimestamperBuildWrapper']) {
          tool name: 'Default', type: 'git'
          echo 'Verify..'
          sh 'chef-client -o sdlc_structure::verify'
        }
      }
    }
    stage('Clean') {
      steps {
        echo 'Clean..'
          sh 'chef-client -o sdlc_structure::clean'
      }
    }
    stage('Unpack') {
      steps {
        echo 'Unpack..'
        sh 'chef-client -o sdlc_structure::unpack'
      }
    }
    stage('Prepare') {
      steps {
        echo 'Prepare..'
        sh 'chef-client -o sdlc_structure::prepare'
      }
    }
    stage('Build') {
      steps {
          echo 'Building..'
          sh 'chef-client -o sdlc_structure::build'
      }
    }
    stage('Check') {
      steps {
        echo 'Check..'
        sh 'chef-client -o sdlc_structure::check'
      }
    }
    stage('Install') {
      steps {
        echo 'Install..'
        sh 'chef-client -o sdlc_structure::install'
      }
    }
    stage('Strip') {
      steps {
        echo 'Strip..'
        sh 'chef-client -o sdlc_structure::strip'
      }
    }
    stage('End') {
      steps {
        echo 'Finishing..'
        sh 'chef-client -o sdlc_structure::end'
      }
    }
  }
  post {
    always {
        sh 'rspec --format progress --format RspecJunitFormatter --out rspec.xml'
    }
    failure {
        echo 'The Pipeline failed :('
    }
  }
}
