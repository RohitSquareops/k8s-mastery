pipeline{
agent any
  environment{
    Image_Repo="rohitsquareops"
    Branch="master"
    Docker_Cred=credentials('docker-cred')
  }
stages{
  stage('Go to repo'){
    steps{
      container('docker'){ 
        script{
             echo "take code from github"
             sh   '''
              git clone -b $Branch https://github.com/RohitSquareops/k8s-mastery.git
             '''
             echo "Branch copied"
        }
      }
    }
  }	
  }
  }
