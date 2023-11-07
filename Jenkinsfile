node {
    stage('Git checkout') {
        git 'https://github.com/9895sagar/Kubernetes_Project.git'
    }
    
    stage('sending docker file to Ansible server over ssh') {
        sshagent(['ansible_demo']) {
         echo 'Connecting via SSH...'
         sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.38.70'
         echo 'Copying files...'
         sh 'scp /var/lib/jenkins/workspace/pipeline-demo/* ubuntu@172.31.38.70:/home/ubuntu'
      }
    }
}
