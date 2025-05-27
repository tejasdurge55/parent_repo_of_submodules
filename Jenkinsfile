pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([
          $class: 'GitSCM',
          branches: [[name: master]],
          doGenerateSubmoduleConfigurations: false,
          extensions: [[$class: 'SubmoduleOption', recursiveSubmodules: true, trackingSubmodules: true]],
          submoduleCfg: [],
          userRemoteConfigs: [[
            url: 'https://github.com/tejasdurge55/parent_repo_of_submodules.git',
            credentialsId: 'github-creds'
          ]]
        ])
      }
    }

    stage('Pull Submodule Updates') {
      steps {
        sh '''
          git submodule update --remote --merge
          git status
        '''
      }
    }

    // Add your actual build/test/deploy steps here
  }
}
