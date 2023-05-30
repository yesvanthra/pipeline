node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonar-scanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
      sh " sonar-scanner -Dsonar.projectKey=pipeline -Dsonar.sources=/var/jenkins_home/workspace/hut -Dsonar.host.url=http://172.18.0.3:9000   -Dsonar.login=sqp_eed20e39e9f568a19d56eeb4b6fad6cf20f58ea9"
    }
  }
}
