pipeline{
  agent{
    label "worker1"
  }
  stages{
    stage("build-ngnix"){
      steps{
        sh '''
        docker build -t myngnix1 -f myngnix.DockerFile .
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
