pipeline {
    agent any
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/opsgauraw/testcicd.git'
             
          }
        }
  stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
   stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t opsgauraw/testwebapp .' 
                sh 'docker tag opsgauraw/testwebapp opsgauraw/testwebapp:latest'
                //sh 'docker tag testwebapp opsgauraw/testwebapp:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'      
        //withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
          sh  'docker push opsgauraw/testwebapp:latest'
        //  sh  'docker push opsgauraw/testwebapp:latest' 
        }
                  
          }
        }
     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
   {
                sh "docker run -d -p 8090:8080 opsgauraw/testwebapp:latest"
 
            }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                echo "We will try this also"
                //sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 8003:8080 opsgauraw/testwebapp"
 
            }
        }
    }
 }
