pipeline{
  agent{
    label "awsworker"
  }
  stages{
    stage("build-ngnix"){
      steps{
        sh '''
        pwd
        ls -ltr
        docker build -t myngnix1 -f myngnix.Dockerfile .
        docker images | grep myngnix1
        '''
      }
    }
    stage("run-ngnix"){
      steps{
        sh '''
        docker rm -f myngnix1 | exit 0
        docker run -d -p 8083:80 --name myngnix1 myngnix1
           '''
      }
    }
    
  }
}
