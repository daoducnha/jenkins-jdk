pipeline {
    agent any 
    
    stages {
        stage('Build') { 
            steps {
                withMaven(
                    maven: 'jenkins-maven',
                    jdk: 'JDK 8'
                    ) {
                        sh 'echo "Building....."'
                        sh '''
                            mvn clean package
                        '''
                    }
            }
        }
        stage('Test') { 
                steps {
                    withMaven(
                        maven: 'jenkins-maven',
                        jdk: 'JDK 8'
                    ) {
                        echo "Testing......" 
                        sh 'mvn test'
                    }
            }
        }
        stage('Deploy') { 
            steps {
                sh '''
                    java -jar target/*.jar
                '''
            }
        }
        
    }
    
}