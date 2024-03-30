pipeline {
    agent any
    environment {
        // Define a variable to store the secret text
        discordWebhookUrl = credentials('my_jenkin_announcementss')
    }
    stages {
        stage("Clone Git Repository") {
            steps {
                git(
                    url: "https://github.com/Project-for-myself/Terraform.git",
                    branch: "dev",
                    changelog: true,
                    poll: true
                )
            }
        }
        
        stage('List Files') {
            steps {
                // show all files from the repository
                script {
                    sh 'ls -la'
                }
            }
        }
        
        stage('Send Discord Message') {
            steps {
                // Send a message to Discord
                script {
                    def message = "SUCCESS"
                    if (message == "SUCCESS") {
                        message = "Pipeline completed successfully ! _🔥🔥🔥_"
                    } else {
                        message = "Pipeline is unsuccessful ! _😭😭😭_ (Something went wrong)"
                    }

                    sh "curl -X POST -H 'Content-Type: application/json' -d '{\"content\": \"${message}\"}' \"${discordWebhookUrl}\""
                    // 14
                    
                }
            }
        }
    }
}