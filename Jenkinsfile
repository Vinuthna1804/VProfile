pipeline {
    agent any

    stages {
        stage('git_clone') {
            steps {
                git 'https://github.com/Vinuthna1804/VProfile.git'
            }
        }
    stage('maven build') {
            steps {
                sh 'mvn package'
            }
        }
    stage('nexus') {
           steps {
               //nexus upload artifact 
                nexusArtifactUploader artifacts: [[artifactId: 'vprofile', classifier: '', file: 'target/vprofile-v1.war', type: 'war']], credentialsId: '4e89fbdb-21c2-4d7d-bc14-69fd4aa96e5d', groupId: 'NEW', nexusUrl: '172.31.33.188:8080/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'vprofile', version: '$BUILD_ID'
                  }
         }
    stage('deploy to tomcat'){
           steps {
             deploy adapters: [tomcat8(credentialsId: '724552ed-9382-4b80-987c-f93a0446d8e8', path: '', url: 'http://172.31.47.209:8081')], contextPath: 'vprofile', war: 'target/vprofile-v1.war'
}
}
    }
}
