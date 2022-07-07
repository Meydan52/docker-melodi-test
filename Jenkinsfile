node("docker"){
    stage("Test"){
        checkout scm // clones every thing from the branch (gives file names in the repo)
        sh "ls"

    }
    stage("Build"){
        sh "docker build -t test ."
    }
}