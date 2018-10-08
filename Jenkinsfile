import jenkins.model.*

pipeline {
    // run on jenkins nodes tha has java 8 label
    agent any
    // global env variables
    environment {
        EMAIL_RECIPIENTS = 'kumarstaffings@gmail.com'
    }
    stages {

        stage('Build with unit testing') {
            steps {
                // Run the maven build
                script {
                    // Get the Maven tool.
                    // ** NOTE: This 'M3' Maven tool must be configured
                    // **       in the global configuration.
                    echo 'Pulling...' + env.BRANCH_NAME
                    def mvnHome = tool name: 'Maven', type: 'maven'
                   
     bat(/"${mvnHome}\bin\mvn" -Dintegration-tests.skip=true clean package/)
                       
                                      
                        junit '**//*target/surefire-reports/TEST-*.xml'
                        archive 'target*//*.jar'
                    }
                }

            }
        }
}

