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
        ARTIFACTORY_CREDS = credentials('LinUsrPwd')
    }

    stages {
        stage('Build') {
            steps {
                // We use the -s flag to point to our project-specific settings.xml
                // which uses the environment variables for authentication.
                // Using -X (debug) and -U (force update) to see JFrog status in logs
                sh 'mvn clean install -U -s settings.xml'
            }
        }
    }
}
