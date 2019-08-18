pipeline {
    agent any
    tools {
        jdk 'JDK12.0.2'
        maven 'Maven3.6.1'
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
                bat label: '', script: 'mvn clean package'
                // echo "CheckStyle Results Graph"
                // checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
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
//                 timeout(time: 45, unit: 'SECONDS') {
//  input message: 'Can you wait?', ok: 'Yes I will'
// }
                
                echo "This is Deployment phase"
                archiveArtifacts '**/webapp.war'
                // build 'Deployment Job'
            }           
        }
    }
}