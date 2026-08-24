pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'qa', url: 'https://github.com/SivagattuDevops/devops-realtime-project.git', credentialsId: 'github-creds'
            }
        }
        stage('Deploy to prod') {
            steps {
                sshagent(['prod-server-ssh']) {
                    sh '''
                        scp -o StrictHostKeyChecking=no index.html ubuntu@<44.202.212.15>:/tmp/index.html
                        ssh -o StrictHostKeyChecking=no ubuntu@44.202.212.15 "sudo mv /tmp/index.html /var/www/html/index.html"
                    '''
                }
            }
        }
    }
}
