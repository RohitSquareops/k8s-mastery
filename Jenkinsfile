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
           sh  '''
              git clone -b $Branch https://github.com/RohitSquareops/k8s-mastery.git
             '''
             echo "Branch copied"
        }
      }
    }
  } 
  stage('Build Image and push to dockerhub'){
    steps{
      container('docker'){
        script{
          echo "Test code from github"
          sh  ''' 
          cd k8s-mastery/sa-frontend
          echo $Docker_Cred_PSW | docker login -u $Docker_Cred_USR --password-stdin
          docker build -t frontapp .
          docker image tag frontapp $Image_Repo/frontapp:master-${BUILD_NUMBER}
          docker push $Image_Repo/frontapp:master-${BUILD_NUMBER}
          '''
        }
      }
    }
  }
  
  stage("update image tag and save it to "){
    steps{
      container('docker'){
	    withCredentials([gitUsernamePassword(credentialsId: 'git-cred')]) {
         script{
           echo "Test code from github"
           sh ''' 
              cd k8s-mastery/sa-webapp/webapp
              yq e -i '(.image.tag = "'master-${BUILD_NUMBER}'")' values.yaml
	      git config --global user.email "rohit.kumar@squareops.com"
	      git config --global user.name "RohitSquareops"           
	      git add .
	      git commit -m 'updating image tag in github logic app at helm values.yml'
	      git push origin $Branch  
             '''
        }
	   }
      }
    }
  } 
  
  }
  }
