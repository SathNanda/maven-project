pipeline {
    agent any
    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
		    bat "${DOCKER_TOOLBOX_INSTALL_PATH}docker.exe build . -t tomcatwebapp:${env.BUILD_ID}"
            }
        }
    }
}
