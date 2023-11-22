pipeline {
    agent any

    stages {
        stage('git') {
            steps {
                git credentialsId: 'd99d963c-14c8-424e-93d3-ecec924a0d9f', url: 'https://github.com/GULUMAWAKUMA/newai.git/'
            }
        }
        stage('build and push') {
            steps {
                script{
                     def dockerImageName = "newai"
                  
                    bat "docker build -t newai ."
                   withCredentials([usernamePassword(credentialsId: 'd99d963c-14c8-424e-93d3-ecec924a0d9f', passwordVariable: 'USERP', usernameVariable: 'USERN')]) {

                        bat "docker login -u %USERN% -p %USERP%"
                        bat "docker tag $dockerImageName guluma/$dockerImageName"
                        bat "docker push guluma/$dockerImageName"

                    }
                }
            }
        }
    }
}
