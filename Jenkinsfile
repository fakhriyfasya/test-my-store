def scannerHome = tool 'SonarScanner 4.0';

pipeline {
   agent any
   stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-token2', url: 'https://github.com/fakhriyfasya/test-my-store.git']]])
                sh "ls -lart ./*"
            }
        }     
        
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv(credentialsId: 'sonar-token') { // If you have configured more than one global server connection, you can specify its name
                sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
