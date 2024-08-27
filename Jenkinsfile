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


                    script {
                        pwdJenkins = sh(
                                script: "pwd",
                                returnStdout: true
                        )

                        sh (
                                script: "cd ${pwdJenkins}"
                        )

                        jenkinsVerzija = sh (
                                script: "grep -o -P '(?<=serviceWrapperVersion\\=).*(?=)' gradle.properties | tr -d \"[:space:]\"\n",
                                returnStdout: true
                        )

                    }
                }

                dir('ecimer') {
                    checkout changelog: false,
                            poll: false,
                            scm: [
                                    $class           : 'GitSCM',
                                    branches         : [[name: 'master']],
                                    userRemoteConfigs: [[credentialsId: '73b39acd-15fa-4644-a0a3-00455d0d54d4',
                                                         url          : 'https://github.com/tasevskivann/ecimer.git']]
                            ]



                    script {
                        VAR = sh(
                                script: "pwd",
                                returnStdout: true
                        )

                        sh (
                                script: "cd ${VAR}"
                        )

                        ecimerVerzija = sh (
                                script: "grep -o -P '(?<=version\\=).*(?=)' gradle.properties | tr -d \"[:space:]\"\n",
                                returnStdout: true
                        )

                    }
                }

                script{
                    echo "${ecimerVerzija} - ${jenkinsVerzija}"
                }

                script{
                    if(ecimerVerzija < jenkinsVerzija){
                        ecimerVerzija = jenkinsVerzija
                    }
                }


                script{
                    echo "${ecimerVerzija} - ${jenkinsVerzija}"
                }

            }
        }
    }
}

