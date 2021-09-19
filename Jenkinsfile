node {   
    stage('Checkout the dockefile from GitHub') {            
      git branch: 'main', credentialsId: 'fourtimesId', url: 'https://github.com/FourTimes/aks-acr-jenkins.git'        
    }       
    stage('Build the Image and Push to Azure Container Registry') {                
      app = docker.build('jjino/acr-demo')                
      withDockerRegistry([credentialsId: 'acr_credentials', url: 'https://registry.hub.docker.com']) {                
      app.push("${env.BUILD_NUMBER}")                
      app.push('latest')                
     }        
    }        
}
