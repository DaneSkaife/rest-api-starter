pipeline{
environment {
registry = "DaneSkaife/rest-api-starter"
        registryCredentials = "dockerhub_ID"
        dockerImage = "noderest"
    }
    agent any
        stages {
            stage ('Build Docker Image'){
                steps{
                    script {
                        dockerImage = docker.build(registry)
                    }
                }
            }

 

            stage ("Push to Docker Hub"){
                steps {
                    script {
                        docker.withRegistry('', registryCredentials) {
                            dockerImage.push("${env.BUILD_NUMBER}")
                            dockerImage.push("latest")
                        }
                    }
                }
            }
            }
        }