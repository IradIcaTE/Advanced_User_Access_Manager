pipeline {
    agent { label "First" }

    parameters {
        string( name: "USERNAME", defaultValue: "Parth", description: "Enter the username requesting access" )
    }

    environment {
        BLOCKED_USERS = 'admin,root,hacker123,testuser'
    }
    stages {
        stage('Validate Access') {
            steps {
                script {
                    def inputUser = params.USERNAME.trim().toLowerCase()
                    def blockList = env.BLOCKED_USERS.tokenize(,)

                    if (blockList.contains(inputUser)) {
                        error ("Access denied for user: '${inputUser}' - Blocked user.")
                    } else {
                        echo "Access granted to '${inputUser}'. Proceeding with the pipeline."
                    }
                }
            }
        }

        stage("Provision Environment") {
            steps {
                echo "Provisioning environment for ${params.USERNAME}..."
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully for user ${params.USERNAME}."
        }
        failure {
            echo "Pipeline failed due ti blocked username or an error"
        }
    }
}