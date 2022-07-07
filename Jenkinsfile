node("docker"){
    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DH_PASSWORD', usernameVariable: 'DH_USERNAME')]) {
        stage("Build"){
            checkout scm // clones every thing from the branch (gives file names in the repo)
            sh "docker build -t $DH_USERNAME/melodi:latest  ."
        }
       
        stage("Push"){
            sh '''
                docker login -u $DH_USERNAME -p $DH_PASSWORD
                docker Push $DH_USERNAME/melodi:latest
            '''
        }   
    }   
    
} 