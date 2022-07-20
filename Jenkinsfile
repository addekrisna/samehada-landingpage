properties([pipelineTriggers([githubPush()])]) 
pipeline {
    agent any
    stages {
        stage('Build') {
        agent { label "agent1" }
            steps {
              //
                script { echo "Build"
                if (env.BRANCH_NAME == "development")
                
                { 
                sh "docker build -t addekrisna/landingpage:dev-$BUILD_NUMBER . "
                sh "docker push addekrisna/landingpage:dev-$BUILD_NUMBER"

                }else{ 
                sh "docker build -t addekrisna/landingpage:master-$BUILD_NUMBER . "
                sh "docker push addekrisna/landingpage:master-$BUILD_NUMBER"
                
                }
                
                
                }
                
              }
            }
        stage('Test') {
        agent { label "agent1" }
            steps {
              //
                script { echo "Test" }
              }
            }
        stage('Deploy') {
        agent { label "agent1" }
            steps {
              //
                script { echo "Testing Deploy Lagi" }
            }
          }
        }
      }