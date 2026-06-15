pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/shreyash8010/javaapp1.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run') {
            steps {
                sh '''
                pkill -f jar || true
                nohup java -jar target/*.jar &
                '''
            }
        }
    }
}
