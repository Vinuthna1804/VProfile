pipeline {
    agent any

    stages {
        stage('git_clone') {
            steps {
                git 'https://github.com/Vinuthna1804/VProfile.git'
            }
        }
    stages {
        stage('maven build') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
