def app = 'maven-static-code-analysis'
pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
        git(url: 'https://github.com/Aadghrr/jenkins-course/', branch: 'main', poll: true)
        sh 'mvn -f ${app} clean package'

            }
        }
        stage('Test'){
            steps {
                sh 'mvn -f ${app} clean test'
            }
        }
        stage('Site'){
            steps {
        sh 'mvn -f ${app} site'
            }
        }
        stage('Deploy') {
            when { branch 'master' }
            steps {
                archiveArtifacts artifacts: '${app}/**/*.jar'
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
