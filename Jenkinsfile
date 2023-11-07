pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/9895sagar/Kubernetes_Project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build('your/image')
                }
            }
        }

        stage('Send Docker File to Ansible') {
            steps {
                script {
                    sshPublisher(
                        continueOnError: true,
                        failOnError: true,
                        publishers: [
                            sshPublisherDesc(
                                configName: 'yourSSHConfig',
                                transfers: [
                                    sshTransfer(
                                        sourceFiles: 'Dockerfile',
                                        removePrefix: '',
                                        remoteDirectory: '/home/ubuntu'
                                    )
                                ]
                            )
                        ]
                    )
                }
            }
        }
    }
}
