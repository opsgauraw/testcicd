pipeline{
    agent any 
    tools
     {
        maven "Maven"
     }
    environment{
        VERSION = "${env.BUILD_ID}"
    }
    stages{
        stage("Checkout"){
            steps{
               git branch: 'master', url: https://github.com/opsgauraw/testcicd.git
            }
        }
        
       
        }
    }