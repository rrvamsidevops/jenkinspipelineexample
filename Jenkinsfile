pipeline {
    agent any 
     tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven1-Server1"
    stages {
        stage ('SCM for Java Code') {
            steps{
                git changelog: false, url: 'https://github.com/pavansw/simpleMavenJunit.git'
                echo 'Polling to Developers SCM'
            }
        }
        stage ('Maven Compile') {
            steps{
                sh '''mvn clean
mvn compile'''
            }
        }
        stage ('Testing Code') {
            steps {
                sh '''mvn test'''
                echo 'Testing complete with Junit on maven'

            }
        }
        stage ('Package') {
            steps {
            sh 'mvn package'   
            }
        }
        stage ('Publish Test results'){
            steps {
                
    
            junit 'target/surefire-reports/*.xml'
            }
        }
        stage ('Execute Jar'){
            steps{
                sh 'java -jar target/*.jar'
            }
        }
    }
}
