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
        sh 'mvn -f maven-static-code-analysis clean test'
            }
        }
        stage('Site'){
            steps {
        sh 'mvn -f maven-static-code-analysis site'
            }
        }
        stage('Deploy') {
            when { branch 'master' }
            steps {
                archiveArtifacts artifacts: 'maven-static-code-analysis/**/*.jar'
            }
        }
    }
        post {
            always{
                echo 'Hello world'
        }
            failure{
                echo 'Failed'
            }
    }
}
