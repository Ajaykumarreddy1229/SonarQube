pipeline {
    agent any
    
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }
    
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }
    
    stages {
        stage('Checkout') {
            steps {
                # Checkout your Java project from version control
                # For example:
                # git 'https://github.com/your-repo/java-project.git'
            }
        }
        
        stage('Build') {
            steps {
                # Build your Java project
                # For example:
                # sh 'mvn clean install'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                # Run SonarQube analysis
                # Make sure you have SonarQube configured in Jenkins and provide the correct SonarQube server credentials
                
                
                
                # Or using the SonarQube Scanner for Maven:
                # sh 'mvn sonar:sonar'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                # Additional steps to deploy your Java project
                Invoke-Expression "sudo cp target/*war apache-tomcat-path/webapps"
            }
        }
    }
}
