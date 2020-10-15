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
                echo "This is a build without sonarqube "
                withSonarQubeEnv('My SonarQube Server') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.5') {
                        bat 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage("Quality Gate Status Check") {
            steps{
                echo "This is quality gate status check"
                script{
                    withSonarQubeEnv('sonarserver'){
                        bat "mvn sonar:sonar"
                        timeout(time: 1,unit: 'HOURS'){
                            def qg = waitforQualityGate()
                            if(qg.status != 'OK'){
                                error "Pipeline aborted : ${qg.status}"
                            }
                            
                        }
                        bat "mvn clean install"
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
