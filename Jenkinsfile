pipeline {
    agent any 
    
    stages {
        stage('Build') { 
            steps {
                withMaven(
                    maven: 'jenkins-maven',
                    jdk: 'JDK11v2',
                    mavenLocalRepo: '$WORKSPACE/jdk11/.repository'
                    ) {
                        sh 'echo $JAVA_HOME'
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
                        jdk: 'JDK11v2',
                        mavenLocalRepo: '$WORKSPACE/jdk11/.repository'
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