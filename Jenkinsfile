pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yesvanthra/pipeline.git'
            }
        }

        stage('Build') {
            steps {
                // Add your build steps here
                // For example:
                sh 'pip install -r requirements.txt' 
                
                
                sh 'cd /var/jenkins_home/workspace/hut/examples && python main.py build'  // Build the project
                sh 'cd /var/jenkins_home/workspace/hut/fastvector && python vector.py build'
                sh 'cd /var/jenkins_home/workspace/hut/tests && python test_vector.py build'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh '/opt/sonar-scanner/bin/sonar-scanner '
                    sh ' sonar-scanner -Dsonar.projectKey=pipeline -Dsonar.sources=/var/jenkins_home/workspace/hut -Dsonar.host.url=http://172.18.0.3:9000   -Dsonar.login=sqp_eed20e39e9f568a19d56eeb4b6fad6cf20f58ea9'
                }
            }
        }
    }
}
