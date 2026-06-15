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
                rm -rf /var/www/html/* 
               cp -r target/ROOT/* /var/www/html/ 
               sudo systemctl restart apache2
                '''
            }
        }
    }
}
