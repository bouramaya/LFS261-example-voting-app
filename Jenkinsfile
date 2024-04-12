#!groovy

node {
    try {
       checkout scm

       /*  stage('three') {
            if (env.BRANCH_NAME == 'master') {
                echo 'step 3'
                sleep(5)
            }
        } */

        docker.image('maven:3.8.3-jdk-8-slim').inside {
             stage("Build") {
                 sh 'mvn -B -f ./worker/pom.xml clean compile'
             }
             stage("Test") {
                 sh 'mvn -B -f ./worker/pom.xml test'
             }
        }
    } catch(err){
        // here you can do any error handling
        println("Error: " + err.toString())
    } finally {
        println('This pipeline is completed.')
    }
}