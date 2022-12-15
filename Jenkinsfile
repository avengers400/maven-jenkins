node {
  stage ('SCM checkout') {
    git 'https://github.com/avengers400/maven-jenkins.git'
  }
  stage ('Compile and package') {
    ///get maven homepath
     def mvnhome = tool name: 'maven-3', type: 'maven'
    sh "${mvnhome}/bin/mvn package"
  }
  stage ('Build Docker Image') {
      docker build . -t rishav/myapp:2.0.0
  }
 
  stage ('Push to DockerHub') {
    //storing docker hub password in global credential section in jenkins
    withCredentials([string(credentialsId: '', variable: 'dockerpwd')]) {
      sh "docker login -u rishav23 -p ${dockerpwd}"
      
}
    docker push rishav/myapp:2.0.0
  }
  stage ('Depoy to target server')
  def dockerdeploy = 'docker run -p 8080:8080 --name myapp rishav/myapp:2.0.0'
  sshagent(['deploy-dev']) {
    sh "ssh -o strictHostKeyChecking=no ec2-user@1.2.3.4 ${dockerdeploy}"
}
  
}
