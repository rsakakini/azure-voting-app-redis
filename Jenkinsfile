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
                  sh '''cd azure-vote/
                        docker images -a
                        docker build -t jenkins-pipeline .
                        cd ..
                     '''
               }
        }
    }
}