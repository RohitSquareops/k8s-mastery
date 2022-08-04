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
           sh
	     '''
              git clone -b $Branch https://github.com/RohitSquareops/k8s-mastery.git
             '''
             echo "Branch copied"
        }
      }
    }
  } 
//   stage('Build Image and push to dockerhub'){
//     steps{
//       container('docker'){
//         script{
//           echo "Test code from github"
//           sh 
//           ''' 
//           cd k8s-mastery/sa-frontend
//           echo $Docker_Cred_PSW | docker login -u $Docker_Cred_USR --password-stdin
//           docker build -t frontend .
//           docker image tag frontend $Image_Repo/frontapp
//           docker push $Image_Repo/frontapp
//           '''
//         }
//       }
//     }
//   }
  
  }
  }
