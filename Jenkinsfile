pipeline {
    agent any

    stages {
        stage("Clean up") {
            steps {
                deleteDir()
            }
        }

        stage("Clone repo") {
            steps {
                sh 'git clone https://github.com/dalyx24/tp2jenkins.git'
            }
        }

        stage("Generate image") {
            steps {
                dir("tp2jenkins") {
                    sh 'mvn clean install'
                    sh 'docker build -t tp2jenk .'
                }
            }
        }

        stage("Run docker compose") {
            steps {
                dir("tp2jenkins") {
                    sh 'docker compose up -d'
                }
            }
        }
    }
}

