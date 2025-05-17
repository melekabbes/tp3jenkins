pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {
        stage("Clean up") {
            steps {
                deleteDir()
            }
        }

        stage("Clone repo") {
            steps {
                bat "git clone https://github.com/melekabbes/tp3jenkins.git"
            }
        }

        stage("Generate backend image") {
            steps {
                dir("tp3jenkins") {
                    bat "mvn clean install"
                    bat "docker build -t tp3jenkins ."
                }
            }
        }

        stage("Run docker compose") {
            steps {
                dir("tp3jenkins") {
                    bat "docker-compose up -d"
                }
            }
        }
    }
}
