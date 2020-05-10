pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: 'localhost', description: 'Staging Server')
         
    }

    triggers {
         pollSCM('* * * * *')
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
                        bat "copy -i  C:\Program Files (x86)\Jenkins\workspace\FullyAutomated\webapp\target\*.war tomcat@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
                    }
                }

               
            }
        }
    }
}