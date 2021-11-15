 pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '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',
                            url: 'https://github.com/mahmoudnouri07/Myapp.git']]])
                }
            }
        } 
stage('npm-Install') {
             steps{
                script{
                    sh "sudo npm install"
                }
            }
        }

stage('build') {
steps{

script {

sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml "

}
}
}         
        
        
               stage('docker')
{
                  steps {
                         script{
                         sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml "
                                }
                        }
  }
  stage('docker_registry') {
steps{
script {


sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml "


}
}
}
        }
        }
