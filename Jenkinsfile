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
         stage('nexus upload') {
             steps {
                //upload artifact to nexus
              nexusArtifactUploader artifacts: [[artifactId: 'vprofile', classifier: '', file: 'target/vprofile-v1.war', type: 'war']], credentialsId: '3e5950bf-953e-4093-8efa-399da460fa98', groupId: 'UAT', nexusUrl: '65.1.136.234:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'vprofile', version: '$BUILD_ID'
           }
        }
          stage('deploy tomcat') {
             steps {
                //deploy artifact to tomcat
                 deploy adapters: [tomcat8(credentialsId: '4485f4f6-c6c8-4274-a3bd-dcdceac0f352', path: '', url: 'http://172.31.41.74:8080')], contextPath: 'tomcat', war: 'target/vprofile-v1.war'
           }
        }
    }
}

