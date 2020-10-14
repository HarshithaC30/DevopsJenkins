node{
  stage('SCM Checkout'){
    git 'https://github.com/HarshithaC30/DevopsJenkins.git'
  }
  stage('Complie-Package'){
    def mvnHome = tool name: '', type: 'maven'
    sh "${mvnHome}/bin/mvn package"
  }
}
