node {
   def mvnHome
  stage('Prepare') {
      git url: 'https://github.com/Vishnu-Yadav0/project.git', branch: 'main'
      mvnHome = tool 'maven'
   }
  stage ('Code Scanning') {
      sh "'${mvnHome}/bin/mvn' sonar:sonar"
  }
  stage ('Clean') {
      sh "'${mvnHome}/bin/mvn' clean"
  }
  stage ('Validate') {
      sh "'${mvnHome}/bin/mvn' validate"
  }
  stage ('Compile') {
      sh "'${mvnHome}/bin/mvn' compile"
  }
  stage ('Test') {
      sh "'${mvnHome}/bin/mvn' test"
  }
  stage ('Install') {
      sh "'${mvnHome}/bin/mvn' install"
  }
  stage ('Verify') {
      sh "'${mvnHome}/bin/mvn' verify"
  }
  stage ('Package') {
      sh "'${mvnHome}/bin/mvn' package"
  }
  stage ('Deploy') {
      sh "'${mvnHome}/bin/mvn' deploy"
  }
  stage ('Deliver & Deployment') {
      sh 'curl -u admin:linux@123 -T target/**.war "http://52.66.167.53:8080/manager/text/deploy?path=/devops&update=true"'
  }
  stage ('SmokeTest') {
      sh 'curl --retry-delay 10 --retry 5 "http://52.66.167.53:8080/devops"'
  }
}