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
               sh "git clone https://github.com/opsgauraw/testcicd.git"
            }
        }
        }
    }
