pipeline {
    agent any
    tools {
        jdk 'Java8'
        maven 'Maven3'
    }
    stages {
        stage ('First Level'){
            steps {
                echo "This is First Level"
            }
        }
        stage  ('Second Level'){
            steps {
                echo "This is Second Level"
                echo "CheckStyle Check"
                sh label: '', script: 'mvn clean package checkstyle:checkstyle'
                    echo "CheckStyle Results Graph"
                checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
            }
            post {
                success {
         echo "Test Result Trend"
                junit '**/surefire-reports/*.xml'
                }
            }               
        }
        stage ('Deploy'){
            steps {
                echo "This is Deployment phase"
                archiveArtifacts '**/webapp.war'
                build 'Deployment Job'
            }           
        }
    }
}