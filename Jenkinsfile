pipeline {
    agent any 
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/HarshithaC30/DevopsJenkins'
            }
        }
        stage('Build && SonarQube analysis') { 
            steps {
                echo "This is a build process without sonarqube "
                withSonarQubeEnv('My SonarQube Server') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.5') {
                        bat 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
                echo "This is quality gate stage"
                timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage('Test') { 
            steps {
                echo "This is test process" 
            }
        }
        stage('Deploy') { 
            steps {
                echo "This is a deploy stage" 
            }
        }
    }
}
