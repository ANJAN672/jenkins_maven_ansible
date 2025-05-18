pipeline {
    agent any

    tools {
        maven 'Default'   // Use the pre-installed or system default Maven
        jdk 'Default'     // Use the pre-installed or system default JDK
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/ANJAN672/jenkins_maven_ansible.git'
            }
        }

        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                sh 'ansible-playbook -i ansible/inventory.ini ansible/deploy.yml'
            }
        }
    }
}
