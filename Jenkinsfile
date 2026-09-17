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

        stage('Copy WAR') {
            steps {
                sh '''
                    scp -i /var/lib/jenkins/.ssh/id_ed25519 \
                    target/war-learning.war \
                    tomcat@172.31.26.129:/tmp/
                '''
            }
        }

    }
}
