pipeline {
    agent any

    tools {
        maven 'Maven 3'   // Use exact name configured in Jenkins Global Tools
        jdk 'Java 17'     // Same here
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
