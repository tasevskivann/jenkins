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
                                    userRemoteConfigs: [[credentialsId: 'my-username-password-id',
                                                         url: 'https://github.com/tasevskivann/jenkins.git']]
                            ]
                }


            }
        }
    }
}

