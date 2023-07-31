pipeline{
    agent any{
        stages{
            stage('fetch code from github')
                steps{
                    git branch: 'main', url: 'https://github.com/sachitbali/ultimate-cicd.git'
                    }
            stage('Build and test'){
                steps{
                    sh 'ls-ltr'
                    //build the project and test
                    sh 'cd ultimate-cicd && mvn clean package '
                }
            }
            stage('test the code'){
                environment{
                    SONAR_URL = "http://52.62.218.244:9000/"
                    }
                steps{
                    withCredentials([string(credentialsId: 'Sonarcloud ', variable: 'SONAR_AUTH_TOKEN')]) {
                    SH 'cd ultimate-cicd && mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
                    }
                
                }
            }
        }





    }
}
