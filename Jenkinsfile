#!/usr/bin/groovy

pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {

                cleanWs()

                dir('jenkins') {
                    checkout changelog: false,
                            poll: false,
                            scm: [
                                    $class           : 'GitSCM',
                                    branches         : [[name: 'master']],
                                    userRemoteConfigs: [[credentialsId: '73b39acd-15fa-4644-a0a3-00455d0d54d4',
                                                         url          : 'https://github.com/tasevskivann/jenkins.git']]
                            ]
                }

                script {
                    VAR = sh(
                            script: "pwd",
                            returnStdout: true
                    )

                    echo "${VAR}"

                    sh (
                            script: "cd ${VAR}"
                    )

                    echo "pwd"
                }


            }
        }
    }
}

