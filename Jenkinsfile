pipeline {
    agent {
        label 'maven-salve'
    }
    tools {
        maven 'Maven-3.9.2'          // Jenkins tool name for Maven
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
            steps {
                withSonarQubeEnv('SonarQube-Server') {   // must match Jenkins global config
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}