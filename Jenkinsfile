#!groovy

node {
    try {
        stage('one') {
            echo 'step 1'
            sleep(3)
        }
        stage('two') {
            echo 'step 2'
            sleep(9)
        }
        stage('three') {
            if (env.BRANCH_NAME == 'master') {
                echo 'step 3'
                sleep(5)
            }
        }
         stage("Build") {
                docker.image('maven:3.8.3-jdk-8-slim').inside {
                    sh 'mvn -B -f ./worker/pom.xml clean compile'
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