pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn test'
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
