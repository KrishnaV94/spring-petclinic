pipeline {
    agent { label ('JDK11') }
    stages {
        stage ('SourceCodeManagement') {
        steps {
            //Pull the code from the Git repo from main branch
            git branch: 'main', url: 'https://github.com/KrishnaV94/spring-petclinic.git'
            }
        }
        stage ('Build/package the code') {
            steps {
                //package the code using maven
                sh 'mvn clean package'
            }
        }
        stage ('Publish jUnit test results') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage ('Archive the Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
            }
        }
    }
}
