pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Curl') {
            steps {
                sh 'curl "http://worldtimeapi.org/api/timezone/Europe/Dublin"'
            }
        }
    }
}
