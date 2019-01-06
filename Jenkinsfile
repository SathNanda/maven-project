pipeline {
    agent any
    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
		bat "'C:/Software/DockerToolbox/'docker.exe build . -t tomcatwebapp:${env.BUILD_ID}"
            }
        }
    }
}
