pipeline {
    agent any

    tools {
        // Ensure this Maven tool is configured in your Jenkins "Global Tool Configuration"
        maven 'maven' 
        jdk 'Java-21'
    }

    environment {
        // You should define these credentials in Jenkins Credentials Manager
        // and bind them here.
        ARTIFACTORY_CREDS = credentials('7e59b761-7e86-402e-bc24-a194c787a656') 
        ARTIFACTORY_USER = "${ARTIFACTORY_CREDS_USR}"
        ARTIFACTORY_PASSWORD = "${ARTIFACTORY_CREDS_PSW}"
    }

    stages {
        stage('Build') {
                // We use the -s flag to point to our project-specific settings.xml
                // which uses the environment variables for authentication.
                // Using -X (debug) and -U (force update) to see JFrog status in logs
                sh 'mvn -X -U clean install -s settings.xml'
        }
    }
}
