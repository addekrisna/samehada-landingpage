properties([pipelineTriggers([githubPush()])]) 
pipeline {
    agent any
    stages {
        stage('Build') {
          agent { label "agent1" }
            steps {
              //
                script { echo "Build"
                if (env.BRANCH_NAME == "develop")
                
                { 
                sh "docker build -t addekrisna/landingpage:dev-$BUILD_NUMBER . "
                sh "docker push addekrisna/landingpage:dev-$BUILD_NUMBER"

                }else{ 
                sh "docker build -t addekrisna/landingpage:main-$BUILD_NUMBER . "
                sh "docker push addekrisna/landingpage:main-$BUILD_NUMBER"
                
                }
                
                
                }
                
              }
            }
        stage('Test') {
          agent { label "agent1" }
            steps {
              //
                script { echo "Test" 
                def scannerHome = tool 'sonarscanner1' ;
	              withSonarQubeEnv('sonarserver1') {
	              sh "${scannerHome}/bin/sonar-scanner"
	                }
                }
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
