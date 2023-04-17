pipeline {
    agent any 
    
    environment {
        NAME = "DUC"
        LAST_NAME = "NHA"
    }
    stages {
        stage('Build') { 
            steps {
                sh 'echo "Building....."'
                sh '''
                    echo "Hello $NAME $LAST_NAME"
                    ls -lah
                '''
            }
        }
        stage('Test') { 
            steps {
                echo "Testing......" 
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deloying....."
            }
        }
        stage('Timeout') { 
            steps {
                retry(3) {
                    sh 'I not going to work :(('
                }
                
            }
        }
    }
    post {
        always {
            echo "I will alway run "
        }
        success {
            echo "I success"
        }
        failure {
            echo "I on failure"
        }
        unstable {
            echo "I on unstable"
        }
    }
}