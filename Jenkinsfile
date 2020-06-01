pipeline {
    agent any

 

stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
				bat 'docker build . -t tomcatwebapps:${env.BUILD_ID}'
            }

        }

   
    }
}