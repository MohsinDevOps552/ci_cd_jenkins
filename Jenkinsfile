pipeline {
    agent {
        label 'maven-salve'
    }

    stages {
        stage('git') {
            steps {
                git branch: 'main', url: 'https://github.com/MohsinDevOps552/ci_cd_jenkins.git'
            }
        }
    }
}
