pipeline {
    agent any
    stages {
        stage ("Pull") {
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                    userRemoteConfigs: [[
                        credentialsId: '1b3edb8c-957f-401f-a039-0288a69058b3',
                        url: 'https://github.com/rayenhedfi/CD_Angular']]])
                }
            }
        }
         stage('Check Python Version'){
            steps{
                script{
                    sh "python3 --version"
                }
            }
        }
         stage('Build'){
            steps{
                script{
                    sh "ANSIBLE_DEBUG=1 ansible-playbook ansible/build.yml -i ansible/inventory/host.yml -e "ansible_become_password=rayen"
                }
            }
        }
}
}
