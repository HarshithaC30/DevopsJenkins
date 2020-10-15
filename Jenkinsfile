pipeline{
    agent any
    stages{
        stage('checkout'){
		echo "Checkout stage"
            steps{
               git 'https://github.com/HarshithaC30/DevopsJenkins'
            }
        }
        stage('Build'){
		echo "Build stage"
            steps{
               bat 'mvn clean package'
            }
            post{
                success{
                    echo 'Now Archiving...build'
                    //archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('SonarQube analysis') {
		echo "SonarQube analysis stage"
            steps{
                withSonarQubeEnv('sonar'){
                   bat 'mvn sonar:sonar'
                }
            }
	}
        
     }
	
	
    } 
