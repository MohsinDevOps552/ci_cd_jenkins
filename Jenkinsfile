pipeline {
    agent {
        label 'maven-salve'
    }
    environment {
        PATH = "/opt/apache-maven-3.9.2/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                echo '----------- build started ----------'
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo '----------- build completed ----------'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                Scannerhome = tool 'Sonar Scanner'
            }
            steps {
                withSonarQubeEnv('SonarQub-server') {
                    sh '$Scannerhome/bin/sonar-scanner'
                }
            }
        }
    }
}