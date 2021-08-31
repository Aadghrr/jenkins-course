pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
        git(url: 'https://github.com/Aadghrr/jenkins-course/', branch: 'main', poll: true)
        sh 'mvn -f maven-static-code-analysis clean package'

            }
        }
        stage('Test'){
            steps {
        git(url: 'https://github.com/Aadghrr/jenkins-course/', branch: 'main', poll: true)
        sh 'mvn -f maven-static-code-analysis clean test'
            }
        }
        stage('Deploy') {
            steps {
                archiveArtifacts artifacts: 'maven-static-code-analysis/target/*.jar'
            }
        }
    }
        post {
            always{
                echo 'Hello world'
        }
    }
}
