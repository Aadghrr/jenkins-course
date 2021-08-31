pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                maven (
                    sh '''cd maven-code-coverage
                           mvn clean package''')
            }
        }
        stage('Test'){
            steps {
                maven (
                    sh ''' mvn clean package''')
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
