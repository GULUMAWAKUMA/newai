pipeline {
    agent any

    stages {
        stage('git') {
            steps {
                git branch: 'main', url: 'https://github.com/naolatomsa/newai'
            }
        }
        stage('build and push') {
            steps {
                script{
                  
                    bat "docker build -t newai ."
                    withCredentials([string(credentialsId: 'Do-na', variable: 'dockerHub_cred')]) {
                     // Define the Docker tag using the build number
         
                        bat "docker tag newai guluma/newai"
                        bat "docker push guluma/newai"
                    }
                }
            }
        }
    }
}
