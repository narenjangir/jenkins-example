pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven') {
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
}
