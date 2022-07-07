if (env.BRANCH_NAME == 'master'){
    tag = "latest"
}
else{
    tag=env.BRANCH_NAME
}
node("docker"){
    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DH_PASSWORD', usernameVariable: 'DH_USERNAME')]) {
        stage("Build"){
            checkout scm // clones every thing from the branch (gives file names in the repo)
            sh "docker build -t $DH_USERNAME/melodi:${tag}  ."
        }
       
        stage("Push"){
            sh '''
                docker login -u $DH_USERNAME -p $DH_PASSWORD
            '''
            sh "docker push $DH_USERNAME/melodi:${tag}"
                
            
        }   
    }   
    
} 