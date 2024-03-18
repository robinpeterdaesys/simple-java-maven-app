pipeline {

    agent any

    tools {
        maven 'maven-3.9.6'
    }

    stages {
        stage('Check-out') {
            steps {
                git credentialsId: 'github-cred-maven-demo', url: 'https://github.com/robinpeterdaesys/simple-java-maven-app.git'
            }
        }

        stage('Build') {
            steps {
                echo "Executing maven build"


                withCredentials([file(credentialsId: 'maven-settings', variable: 'settings')]) {

                    sh "mvn -s $settings clean deploy"

                }
            }

        }
    }
}