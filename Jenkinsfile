pipeline {
    agent any

    environment {
        REMOTE_HOST = '10.203.84.6'
        SSH_CREDENTIALS_ID = 'dlvm'
    }

    stages {
        stage('SSH to Remote Host') {
            steps {
                script {
                    sshagent(credentials: [env.SSH_CREDENTIALS_ID]) {
                        def result = sh(
                            script: """
                                ssh -o StrictHostKeyChecking=no user@${env.REMOTE_HOST} << EOF
                                if [ -f /home/vmware/test.txt ]; then
                                    echo "File exists"
                                    cat /home/vmware/test.txt
                                    exit 0
                                else
                                    echo "File does not exist"
                                    exit 1
                                fi
                                EOF
                            """,
                            returnStatus: true
                        )

                        if (result != 0) {
                            error "SSH command failed with exit status ${result}"
                        } else {
                            echo "SSH command executed successfully"
                        }
                    }
                }
            }
        }
    }
}
