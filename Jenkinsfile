#!/usr/bin/groovy

pipeline{
    agent any
    stages {
        stage('Clone'){
            steps {

                cleanWs()

                dir('copy1'){
                    sh "WORKSPECE - ${env.WORKSPACE}"
                    checkout changelog: false,
                            poll: false,
                            scm: [
                                    $class: 'GitSCM',
                                    userRemoteConfigs: [[credentialsId: 'my-username-password-id',
                                                         url: 'https://github.com/tasevskivann/jenkins.git']]
                            ]
                }

                dir('copy2'){
                    sh "WORKSPECE - ${env.WORKSPACE}"

                    checkout changelog: false,
                            poll: false,
                            scm: [
                                    $class: 'GitSCM',
                                    userRemoteConfigs: [[credentialsId: 'my-username-password-id',
                                                         url: 'https://github.com/tasevskivann/jenkins.git']]
                            ]
                }

                sh "ls -l"
                sh "cd ./copy1 | ls -l"
                sh "cd ./copy2 | ls -l"
            }
        }
    }
}

