pipeline {
    agent {
        docker {
            image 'maven:3.6-openjdk-8'
        }
    }

    triggers {
        pollSCM('*/1 * * * *')
    }

    stages {
        stage ('Maven build') {
            steps {
                sh 'mvn clean install -DskipTests'
                dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'
            }
        }
    }
}
