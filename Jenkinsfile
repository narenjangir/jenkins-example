pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Artifactory') {
            steps{
            rtUpload (
            serverId: "Artifactory",
             spec:
                """{
                 "files": [
                         {
                             "pattern": "*.jar",
                              "target": "generic-local/NJ/"
                         }
                          ]
                     }"""
                )
                }
            }
        }
    }
