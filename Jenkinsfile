pipeline {
agent any

```
tools {
    maven 'maven'
    jdk 'jdk17'
}

stages {

    stage('Checkout') {
        steps {
            git 'https://github.com/shreyash8010/javaapp1.git'
        }
    }

    stage('Build') {
        steps {
            sh 'mvn clean package'
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
```

}
