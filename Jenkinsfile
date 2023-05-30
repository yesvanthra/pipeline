node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonar-scanner';
    withSonarQubeEnv() {
       sh '''

                            /opt/sonar-scanner/bin/sonar-scanner \

                            -Dsonar.projectKey=pipeline \

                            -Dsonar.host.url=http://172.19.0.3:9000 \

                            -Dsonar.login=$SONARQUBE_CRED_USR -Dsonar.password=$SONARQUBE_CRED_PSW

                            '''
    }
  }
}
