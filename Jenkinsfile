#!/usr/bin/groovy

pipeline{
    agent any
    stages {
        stage('Clone'){
            steps {
                sh "ls -l"
                checkout changelog: false,
                    poll: false,
                    scm: [
                            $class: 'GitSCM',
                            doGenerateSubmoduleConfigurations: false,
                            submoduleCfg: [],
                            userRemoteConfigs: [[credentialsId: 'my-username-password-id',
                                                url: 'https://github.com/tasevskivann/jenkins.git']]
                    ]
            }
        }
    }
}

