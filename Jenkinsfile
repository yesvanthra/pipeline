node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
      sh '''

                            /opt/sonar-scanner/bin/sonar-scanner \

                            -Dsonar.projectKey=pipeline \

                            -Dsonar.host.url=http://172.19.0.3:9000 \

                            -Dsonar.login=sqp_eed20e39e9f568a19d56eeb4b6fad6cf20f58ea9 \

                            '''
        
        
        
        
    }
  }
}
