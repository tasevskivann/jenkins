#!/usr/bin/groovy

pipeline{
    agent any
    stages {
        stage('Clone'){
            steps {

                cleanWs()

                dir('copy1'){
                    checkout changelog: false,
                            poll: false,
                            scm: [
                                    $class: 'GitSCM',
                                    branches: [[name: 'master']],
                                    userRemoteConfigs: [[url: 'https://github.com/tasevskivann/ecimer.git']]
                            ]
                }

                sh "ls"


            }
        }
    }
}

