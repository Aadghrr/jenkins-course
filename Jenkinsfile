pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                rtMavenRun (
                    pom: 'maven-code-coverage/pom.xml',
                    goals: 'clean package',
            }
        }
        stage('Test'){
            steps {
                rtMavenRun (
                    pom: 'maven-code-coverage/pom.xml',
                    goals: 'clean test',
            }
        }
        stage('Deploy') {
            steps {
                archiveArtifacts artifacts: 'maven-code-coverage/target/*.jar', fingerprint: true
            }
        }
    }
}
