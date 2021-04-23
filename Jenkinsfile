pipeline {
    agent any

    stages {
        stage('Verify '){
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Build'){
              steps {
                  sh "docker images -a"
                  sh "cd azure-vote/"
                  sh "docker images -a"
                  sh "docker build -t jenkins-pipeline ."
                  sh "cd .."
               }
        }
    }
}