pipeline {
    agent {label "linux"}

    stages {
        stage('Git Clone') {
            steps {
                git 'https://github.com/fakhriyfasya/test-my-store.git'
            }
        }
       
       stage('SonarQube analysis') {
           steps {
               def scannerHome = tool = 'sonarqube';
               withSonarQubeEnv('sonarqube-server') {
                   sh "${scannerHome}/bin/sonar-scanner \
                   -D sonar.login=admin \
                   -D sonar.password=admin123 \
                   -D sonar.projectKey=web-store-app \
                   -D sonar.exclusions=vendor/**,resources/**,**/*.java \
                   -D sonar.host.url=http://34.128.99.9:9000/"
            }       
         }
       }
    }
}
