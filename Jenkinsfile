node {   
    stage('Checkout the dockefile from GitHub') {            
      git branch: 'main', credentialsId: 'fourtimesId', url: 'https://github.com/FourTimes/aks-acr-jenkins.git'        
    }       
    stage('Build the Image and Push to Azure Container Registry') {                
      app = docker.build('testacr.azurecr.io/demo')                
//       withDockerRegistry([credentialsId: 'acr_credentials', url: 'https://testacr.azurecr.io']) {                
//       app.push("${env.BUILD_NUMBER}")                
//       app.push('latest')                
//      }        
    }        
}
