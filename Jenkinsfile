#!/usr/bin/groovy

pipeline{
    agent any
    stages {
        stage('Clone'){
            steps {

                cleanWs()

                dir('jenkins'){
                    checkout changelog: false,
                            poll: false,
                            scm: [
                                    $class: 'GitSCM',
                                    branches: [[name: 'master']],
                                    userRemoteConfigs: [[url: 'https://github.com/tasevskivann/jenkins.git']]
                            ]
                }

                dir('ecimer'){
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

