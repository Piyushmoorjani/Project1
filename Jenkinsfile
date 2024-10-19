pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                // Cloning the GitHub repository
                git branch: 'master', url: 'https://github.com/Piyushmoorjani/Project1.git'
            }
        }
        
        stage('Deploy to Server') {
            steps {
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'your-server-config', // Create an SSH config for your server
                            transfers: [
                                sshTransfer(
                                    sourceFiles: 'index.html',
                                    removePrefix: '',
                                    remoteDirectory: '/var/www/html',
                                    execCommand: 'sudo systemctl restart httpd'
                                )
                            ]
                        )
                    ]
                )
            }
        }
    }
}

