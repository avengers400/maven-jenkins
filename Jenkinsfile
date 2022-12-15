node {
  stage ('SCM checkout') {
    git 'https://github.com/avengers400/maven-jenkins.git'
  }
  stage ('Compile and package') {
     sh 'mvn clean package'
  }
}
