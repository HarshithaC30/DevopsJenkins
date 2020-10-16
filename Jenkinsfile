pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
		    echo "Checkout stage"
               git 'https://github.com/HarshithaC30/DevopsJenkins'
            }
        }
        stage('Build'){
            steps{
		    echo "Build stage"
               bat 'mvn clean package'
            }
            post{
                success{
                    echo 'Now Archiving...build stage'
                }
            }
        }
        stage('SonarQube analysis') {
            steps{
		    echo "SonarQube analysis stage"
                withSonarQubeEnv('sonar'){
                   bat 'mvn sonar:sonar'
                }
            }
	}
        
     }
	
	
    } 
