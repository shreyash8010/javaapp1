pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/shreyash8010/javaapp1.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
               echo "Checking Tomcat webapps directory..."

                ls -ld /var/lib/tomcat10/webapps || exit 1

                cp target/ROOT.war /var/lib/tomcat10/webapps/ROOT.war

                sudo systemctl restart tomcat10
                '''
            }
        }
    }
}
