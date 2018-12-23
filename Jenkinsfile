pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: '3.17.161.209', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '3.17.149.43', description: 'Production Server')
    }

stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
 
        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        bat "pscp -i C:/Software/cmder/tomcat-demo.ppk '%programfiles(x86)%/Jenkins/workspace/FullyAutomated/webapp/target/*.war' ec2-user@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
                    }
                }
 
                stage ("Deploy to Production"){
                    steps {
                        bat "pscp -i C:/Software/cmder/tomcat-demo.ppk '%programfiles(x86)%/Jenkins/workspace/FullyAutomated/webapp/target/*.war' ec2-user@${params.tomcat_prod}:/var/lib/tomcat7/webapps"
                    }
                }
            }
        }
    }
}
