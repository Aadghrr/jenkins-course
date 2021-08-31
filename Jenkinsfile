pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                maven (
                    pom: 'maven-code-coverage/pom.xml',
                    goals: 'clean package'
                    )
            }
        }
        stage('Test'){
            steps {
                maven (
                    pom: 'maven-code-coverage/pom.xml',
                    goals: 'clean test',
                   )
            }
        }
        stage('Deploy') {
            steps {
                archiveArtifacts artifacts: 'maven-code-coverage/target/*.jar'
            }
        }
    }
        post {
            always{
                echo 'Hello world'
        }
    }
}
