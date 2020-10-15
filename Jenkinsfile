pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
               git 'https://github.com/HarshithaC30/DevopsJenkins'
            }
        }
        stage('Build'){
            steps{
               bat 'mvn clean package'
            }
            post{
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('SonarQube analysis') {
            steps{
                withSonarQubeEnv('sonar'){
                   bat 'mvn sonar:sonar'
                }
            }
	}
        
     }
	
	
    } 
