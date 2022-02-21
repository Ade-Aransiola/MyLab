pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }


        // Stage3 : Publish the artifacts to Nexus
        stage ('Publish to Nexus'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'AdeDevOpsLab', classifier: '', file: 'target/AdeDevOpsLab-0.0.7.war', type: 'war']], credentialsId: 'c934b70d-ceda-4b10-9c19-1878f8170a69', groupId: 'com.adedevopslab', nexusUrl: '172.20.10.134:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'AdeDevopsLab-SNAPSHOT', version: '0.0.7'
            }
        }


        // Stage3 : Deploy
        stage ('Deploy'){
            steps {
                echo ' deploy......'

            }
        }
    }

}