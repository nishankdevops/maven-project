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
                sh label: '', script: 'mvn clean package checkstyle:checkstyle'
            }
        }
        stage ('Third Level'){
            steps {
                echo "This is Third Level Finally"
            }           
        }
    }
}