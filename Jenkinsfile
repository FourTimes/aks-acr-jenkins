node {   
    stage('Checkout the dockefile from GitHub') {            
      git branch: 'main', credentialsId: 'fourtimesId', url: 'https://github.com/FourTimes/aks-acr-jenkins.git'        
    }       
    stage('Build the Image and Push to Azure Container Registry') {                
      app = docker.build('migstageacr.azurecr.io/acr-demo')                
      withDockerRegistry([credentialsId: 'acr_credentials', url: 'https://migstageacr.azurecr.io']) {                
      app.push("${env.BUILD_NUMBER}")                
      app.push('latest')                
     }        
    }  
    stage ('kubernetes') {
        withCredentials([kubeconfigFile(credentialsId: 'kube-config', variable: 'KUBECONFIG')]) {
            sh 'kubectl --kubeconfig=$KUBECONFIG get ns'
        }
    }
}
