pipeline {
    agent any
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
                // Виводимо всі файли з репозиторію
                script {
                    sh 'ls -la'
                }
            }
        }
        
        stage('Send Discord Message') {
            steps {
                // Надсилаємо повідомлення в Discord
                script {
                    message = "SUCCESS"
                    if (message == "SUCCESS") {
                        message = "Пайплайн виконаний успішно ! 🔥🔥🔥"
                    } else {
                        message = "Пайплайн завершився Хуйово ! 😭😭😭 (Щось пішло не так)"
                    }
                    
                    def discordWebhookUrl = 'https://discord.com/api/webhooks/1222655463259377724/uk-NlGmSM73LAfp_vt5ym5pMbQuFH6idITp-blinD6AyI9rK_dHUw2xTxAsEJlcfeBn2'
                    sh "curl -X POST -H 'Content-Type: application/json' -d '{\"content\": \"${message}\"}' ${discordWebhookUrl}"
                }
            }
        }
    }
}