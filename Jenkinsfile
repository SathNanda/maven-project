pipeline {
    agent any
    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
		bat ""C:\Program Files\Docker Toolbox\docker.exe" build . -t tomcatwebapp:${env.BUILD_ID}"
            }
        }
    }
}
