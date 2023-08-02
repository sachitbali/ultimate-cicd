pipeline{
    agent any
    tools {
        maven "maven"
        jdk "OracleJDK11"
    }
    stages{
        stage('Fetch Code'){
            steps{
                git branch: 'main', url: 'mention url'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn install -DskipTests'
            }
        }   post{
                success {
                    echo 'Archiving artifacts now.'
                    archiveArtifacts artifacts: '**/*.war'
                }
        }
        stage('Unit Test'){
            steps{
                sh 'mvn test'
            }
        }
    }
}
