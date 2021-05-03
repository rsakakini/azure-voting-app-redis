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
         stage('Start test app'){
                      steps {
                          sh '''
                          docker-compose up -d
                           ./scripts/test_container.ps1
                             '''
                       }

              post('Start test app'){
                     success {
                                echo "App started successfully"
                                }
                     failure {
                                echo "App started successfully"
                                }
              }
              }
          stage('Run tests'){
                       steps {
                           sh '''
                               pytest ./tests/test_sample.py
                            '''
                                }
                         }

           stage('Stop test app'){
                                  steps {
                                      sh '''
                                         docker compose down
                                       '''
                                           }
                                    }
    }
}