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

        stage('Deploy to Tomcat') {
            steps {
                sh '''
                    ssh -i /var/lib/jenkins/.ssh/id_ed25519 \
                    tomcat@172.31.26.129 \
                    'cp /tmp/war-learning.war /opt/tomcat/current/webapps/'
                '''
            }
        }

    }
}
