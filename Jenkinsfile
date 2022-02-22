pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    environment{
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
        Name = readMavenPom().getName()
        GroupId = readMavenPom().getGroupId()
    }


    stages {
        // Specify various stage with in stages

        // stage 1 : Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage 2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }


        // Stage 3 : Publish the artifacts to Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: 
                [[artifactId: 'AdeDevOpsLab', 
                classifier: '', file: 'target/AdeDevOpsLab-0.0.4-SNAPSHOT.war', 
                type: 'war']], credentialsId: 'c934b70d-ceda-4b10-9c19-1878f8170a69', 
                groupId: 'com.adedevopslab', 
                nexusUrl: '172.20.10.134:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'AdeDevopsLab-SNAPSHOT', 
                version: '0.0.4-SNAPSHOT'
            }
        }


        // Stage 4 : Print some information
        stage ('Print Environment variable'){
            steps {
                echo "Artifact ID is '{$ArtifactId}'"
                echo "Version is '{$Version}'"
                echo "GroupID is '{$GroupId}'"
                echo "Name is '{$Name}'"
            }
        }
    }

}