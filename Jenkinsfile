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
                sh '''
                mvn clean package -DskipTests
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Stopping Tomcat..."
                sudo systemctl stop tomcat10

                echo "Removing old application..."
                sudo rm -rf /var/lib/tomcat10/webapps/ROOT
                sudo rm -f /var/lib/tomcat10/webapps/ROOT.war

                echo "Deploying new WAR..."
                sudo cp target/ROOT.war /var/lib/tomcat10/webapps/

                echo "Starting Tomcat..."
                sudo systemctl start tomcat10

                echo "Deployment Successful"
                '''
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}
