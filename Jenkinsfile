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
         stage('Build'){
            steps{
                script{
                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }
        }
}
}
