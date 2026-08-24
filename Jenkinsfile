pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'qa', url: 'https://github.com/SivagattuDevops/devops-realtime-project.git', credentialsId: 'github-creds'
            }
        }
        stage('Deploy to QA') {
            steps {
                sshagent(['qa-server-ssh']) {
                    sh '''
                        scp -o StrictHostKeyChecking=no index.html ubuntu@32.192.235.125:/tmp/index.html
                        ssh -o StrictHostKeyChecking=no ubuntu@32.192.235.125 "sudo mv /tmp/index.html /var/www/html/index.html"
                    '''
                }
            }
        }
    }
}
