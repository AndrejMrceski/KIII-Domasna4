node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("AndrejMrceski/kiii-domasna4".toLowerCase())
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'am-dockerhub') {
            app.push("mrceski/kiii-domasna4-${env.BUILD_NUMBER}")
            app.push("mrceski/kiii-domasna4-latest")
            // signal the orchestrator that there is a new version
        }
    }
}