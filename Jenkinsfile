pipeline {
    agent any

    tools {
        jdk 'jdk-21'
        maven 'maven-ci-server'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

    }
}
