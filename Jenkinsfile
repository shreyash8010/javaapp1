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
            java -version
            mvn -version
            mvn clean package
            '''
        }
    }

    stage('Deploy') {
        steps {
            sh '''
            rm -rf /var/www/html/*
            cp -r target/ROOT/* /var/www/html/
            sudo systemctl restart apache2
            '''
        }
    }
}


}
