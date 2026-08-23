pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'dev', url: 'https://github.com/SivagattuDevops/devops-realtime-project.git', credentialsId: 'github-creds'
            }
        }
        stage('Deploy to Dev') {
            steps {
                sshagent(['dev-server-ssh']) {
                    sh '''
                        scp -o StrictHostKeyChecking=no index.html ubuntu@13.218.180.10:/tmp/index.html
                        ssh -o StrictHostKeyChecking=no ubuntu@13.218.180.10 "sudo mv /tmp/index.html /var/www/html/index.html"
                    '''
                }
            }
        }
    }
}
