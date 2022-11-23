pipeline {
    agent any
    tools {
        gradle 'Gradle-6'
    }
    stages {
        stage ('clone repository'){
            steps {
                git 'https://github.com/Abdihakim-Muhumed/java-todo'
            }
        }
        stage ('Build project'){
            steps {
                sh 'gradle build'
            }
        }
        stage ('Tests') {
            steps {
                sh 'gradle test'
            }
        }
        stage ('Deploy to Heroku') {
            steps {
                withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){
                    sh  'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/fast-reef-77248.git master'
                }   
            }
        }
    }
}