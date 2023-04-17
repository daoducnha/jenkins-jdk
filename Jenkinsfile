pipeline {
    agent any 
    
    stages {
        stage('Build') { 
            withMaven(
                maven: 'jenkins-maven'
                jdk: 'JDK 11'
            )
            steps {
                sh 'echo "Building....."'
                sh '''
                    mvn clean package
                '''
            }
        }
        stage('Test') { 
            withMaven(
                maven: 'jenkins-maven'
                jdk: 'JDK 11'
            )

            steps {
                echo "Testing......" 
                sh 'mvn test'
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deloying....."
            }
        }
        
    }
    
}