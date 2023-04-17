pipeline {
    agent any 
    
    stages {
        stage('Build') { 
            steps {
                maven(
                    maven: 'jenkins-maven',
                    jdk: 'JDK 11'
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
                    maven(
                        maven: 'jenkins-maven',
                        jdk: 'JDK 11'
                    ) {
                        echo "Testing......" 
                        sh 'mvn test'
                    }
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deloying....."
            }
        }
        
    }
    
}