node {
  stage ('SCM checkout') {
    git 'https://github.com/avengers400/maven-jenkins.git'
  }
  stage ('Compile and package') {
    ///get maven homepath
     def mvnhome = tool name: 'maven-3', type: 'maven'
    sh "${mvnhome}/bin/mvn package"
  }
}
