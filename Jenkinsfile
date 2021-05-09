pipeline {
    agent any

    stages {
        stage('git repo clone') {
            steps {
                git 'https://github.com/Vinuthna1804/VProfile.git'
            }
        }
         stage('build') {
             steps {
                //maven packaging
                 sh 'mvn package'
            }
         }
    }
}

