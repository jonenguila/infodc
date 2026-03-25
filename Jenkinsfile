pipeline {
    agent any

    environment {
        APP_DIR = "/opt/docker_projects/supabase/infodc"
        CONTAINER_NAME = "infodc"
    }

    stages {

        stage('Pull do Git') {
            steps {
                dir("${APP_DIR}") {
                    git branch: 'main', url: 'https://github.com/jonenguila/infodc.git'
                }
            }
        }

        stage('Build Docker') {
            steps {
                dir("${APP_DIR}") {
                    sh 'docker compose build'
                }
            }
        }

        stage('Deploy Docker') {
            steps {
                dir("${APP_DIR}") {
                    sh 'docker compose up -d'
                }
            }
        }
    }

    post {
        success {
            echo 'Deploy concluído com sucesso!'
        }
        failure {
            echo 'Ocorreu um erro no pipeline.'
        }
    }
}
